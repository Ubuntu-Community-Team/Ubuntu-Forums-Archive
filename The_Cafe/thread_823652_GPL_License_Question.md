---
title: "GPL License Question"
date: 2008-06-09
forum: The Cafe
---

### Post by Black Mage on 2008-06-09
So I'm reading through the legal documents for GPL and I am little confused and have one question. I know that if you use code that is under the GPL licensed, you are required to release the source code. But if the code is integrated into a program, are you required to release the source code of the program you write and the under the GPL license?

---

### Post by SunnyRabbiera on 2008-06-09
Possibly, depending on the license of the application.

---

### Post by LaRoza on 2008-06-09
> **Black Mage said:**
> So I'm reading through the legal documents for GPL and I am little confused and have one question. I know that if you use code that is under the GPL licensed, you are required to release the source code. But if the code is integrated into a program, are you required to release the source code of the program you write and the under the GPL license?

You don't have to release the source code if the application isn't being distributed.

---

### Post by Black Mage on 2008-06-09
> **LaRoza said:**
> You don't have to release the source code if the application isn't being distributed.

But if it is, you do then.

Basically I'm making a program the requires a MYSQL Driver and Java. and the MySQL driver is licensed under GPL and I am accessing it as an external jar.So, I'm not actually modifying the jar, just using its classes.

And things bring up another one of my question, how does Apple use open source software but not have to open up its source code?

---

### Post by saulgoode on 2008-06-09
If you are creating a closed, proprietary project using MySQL, you should contact Sun about obtaining a commercial license. That is why it is dual-licensed: GPLed projects can use it under the GPL.

---

### Post by Black Mage on 2008-06-09
Ok, and now through reading, correct me if I am wrong, but if you use LGPL then you just have to release the source code under LGPL and not your own?

And then I read this which confuses me even more:

> 
If someone is interested - brief explanation: if you are using GPL software in your software you must distribute yours as GPL, too.

However, you can use LGPL-bistributed software in your commercial applications. LGPL stays for Lesser GPL and is less severe than GPL.

For example, phpmailer and smarty are distributed under LPGL (yep, i was wrong about GPL-Smarty): [http://smarty.incutio.com/?page=SmartyFrequentlyAs](http://smarty.incutio.com/?page=SmartyFrequentlyAs) kedQuestions#other-1
Actually you do not have to GPL anything that has GPL code (IF)

1 - You include the full unmodified source of any gpl code you used in your distribution.

2 - You include the full source of any parts of any code contaning the GPL code.


---

### Post by Mr. Picklesworth on 2008-06-09
If you link GPL code to an application, the terms are rather strict, as you have seen.

LGPLed code, however, can be linked happily without worrying about licenses. For example, GTK is licensed under the Lesser GPL and as a result has seen very widespread adoption with programs that are not GPLed or even open source.
(LGPL does not change much else that I can remember; if the library is directly modified, source must be released with distributions).

I think, as a rule of thumb, a license like LGPL is important for platform-related libraries, while GPL is an acceptable choice for a non-essential library that merely "makes something easier".

---

### Post by Black Mage on 2008-06-09
Then what exactly is GPL-covered program?

---

### Post by LaRoza on 2008-06-09
> **Black Mage said:**
> 
And things bring up another one of my question, how does Apple use open source software but not have to open up its source code?

They do. See Darwin.

---

### Post by Black Mage on 2008-06-09
```

Inclusion of a covered work in an aggregate does not cause this License to apply to the other parts of the aggregate.

```

Does that mean that work included in a larger program does not make the larger program fall into the GPL License?

---

### Post by Black Mage on 2008-06-09
Sorry, this is just to understand this last thing about GPL.

> 
To &#8220;convey&#8221; a work means any kind of propagation that enables other parties to make or receive copies. Mere interaction with a user through a computer network, with no transfer of a copy, is not conveying.


Does this mean that if I have someone connect to a MySQL Database, and MySQL is GPL, but because the database is not on their computer or being copied over, then the program that is used to connect to the database does not fall under GPL?

---

