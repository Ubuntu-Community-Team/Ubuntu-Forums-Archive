---
title: "Ending price in qbasic to be limited to x.xx"
date: 2009-09-08
forum: The Cafe
---

### Post by SpenceMakesSense on 2009-09-08
I made a simple qbasic program that puts you through the process of ordering at a restaurant.  Everything is almost perfect except the ending price is usually something like
$12.2322
Anyone know the code to make it just go to the hundreths spot?(x.xx)(my teacher has no clue)

---

### Post by JillSwift on 2009-09-08
[http://faq.qbasicnews.com/?blast=RoundingNumbers](http://faq.qbasicnews.com/?blast=RoundingNumbers)

Google is your friend.

---

### Post by GeneralZod on 2009-09-08
Floating point maths in computing is inherently error-prone and best avoided if accuracy is required.  Many people do all of the calculations in cents and show this cent amount converted to dollars to the user.

---

### Post by MaxIBoy on 2009-09-08
I don't know how to program BASIC (And I humbly submit that you learn something different because BASIC is awful,) but isn't there a built-in rounding function which lets you select  a specific amount of precision? And if not, shouldn't you be able to multiply by a hundred and convert the number to integer?

If you want to be **really** fancy, you can do something like this:
```

price = price*1000
if price % 10 >= 5: 
    price = price+10
price = price-(price%10)
price = price/1000

```But really, any self-respecting language has something like this:
```

price = round (price, 2) #round to two digits

```Few other considerations:
*This forum is a bad place for homework questions.
*Seriously, your professor doesn't know how to do this? I could have taught you how to do that at age 10. (Actually, I could have done a better job, I knew BASIC back then. :) )




EDIT: GeneralZod is correct, you should do all the math in tenths of a cent (not whole cents, you need a rounding-error digit) and with integers. Integer math runs faster, but more importantly the results are guaranteed to be 100% precise (but not 100% correct, there's a difference.)

---

