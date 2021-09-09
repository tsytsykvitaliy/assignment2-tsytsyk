# assignment2-tsytsyk
Web Apps Assignment 2

# Name: Vitaliy Tsytsyk

## Favorite Location: Greece

I visited Greece during one of the summers and it was amazing. Absoulutely **breathtaking** views, **tasty** foods and **great** culture. Definitely would love to come back!

---

## Travel
How to get to Athens (Greece) from Maryville (Missouri, USA)

1. Take US-71 S and I-29 S to get to Kansas City International Airport (MCI)
2. Take a flight AA 4763 from Kansas City International Airport (MCI) to Chicago O'Hare International Airport (ORD)
3. After a layover, take a flight AA 160 to Athens International Airport (ATH)

What should you bring with you?

- Documents
- Money (Euro)
- Electronics
- Sunscreen
- Beach clothes
- Camera
- Open mind and great mood

More About Me: [AboutMe](AboutMe.md)

---

## Food and Drinks

Here are some Greek foods and drinks that I recommend to try while in Athens, where to buy them and how much to exprect to pay:

|Item|Location|Price|
|---|---|---|
|Baklava|Konstantinidis Pastry|19€/kg|
|Gyros|Bairaktaris Taverna Central|2.70€|
|Frappe|GC George Cafe|1€|
|Retsina Wine|Scholarchio|7€|

---

## Quotes I Like

> “It does not matter how slowly you go as long as you do not stop.”  
> *- Confucius*

> “Our life is what our thoughts make it.”  
> *- Marcus Aurelius*

---

## Primitive Root

> In modular arithmetic, a number g is a primitive root modulo n if every number a coprime to n is congruent to a power of g modulo n. That is, g is a primitive root modulo n, if for every integer a coprime to n, there is some integer k for which gk ≡ a (mod n). Such a value k is called the index or discrete logarithm of a to the base g modulo n. So g is a primitive root modulo n if and only if g is a generator of the multiplicative group of integers modulo n.  
> 
> Source: [Wikipedia Page](https://en.wikipedia.org/wiki/Primitive_root_modulo_n)

Code:

```
int powmod (int a, int b, int p) {
    int res = 1;
    while (b)
        if (b & 1)
            res = int (res * 1ll * a % p),  --b;
        else
            a = int (a * 1ll * a % p),  b >>= 1;
    return res;
}

int generator (int p) {
    vector<int> fact;
    int phi = p-1,  n = phi;
    for (int i=2; i*i<=n; ++i)
        if (n % i == 0) {
            fact.push_back (i);
            while (n % i == 0)
                n /= i;
        }
    if (n > 1)
        fact.push_back (n);

    for (int res=2; res<=p; ++res) {
        bool ok = true;
        for (size_t i=0; i<fact.size() && ok; ++i)
            ok &= powmod (res, phi / fact[i], p) != 1;
        if (ok)  return res;
    }
    return -1;
}
```
Source: [CP-Algorithms](https://cp-algorithms.com/algebra/primitive-root.html)
