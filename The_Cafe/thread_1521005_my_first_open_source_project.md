---
title: "my first open source project"
date: 2010-06-30
forum: The Cafe
---

### Post by sxmaxchine on 2010-06-30
I have released my first open source project today. It is a simple python program that i created to get the ip address of any website. I also added a feature that opens the website using the IP address.

If you would like to try it out or even contribute to the project then you can [check it out here]("http://maxping.webs.com/")

---

### Post by JDShu on 2010-06-30
Just wondering, what do you envision people doing with your program?

---

### Post by Viva on 2010-06-30
Good work for a first project. Try something more advanced this time, onwards and upwards:D

---

### Post by sxmaxchine on 2010-06-30
I am trying to make a program that can help people get information about any website. one of the things i wanted to do was gather your personal Ip address and the sites Ip address.

---

### Post by sxmaxchine on 2010-06-30
Also i figured it might help me with my cert 3 in IT networking.

---

### Post by Simian Man on 2010-06-30
You can also do this with nslookup:
```

nslookup www.google.com | tail -n -3 | grep Address

```

But learning new things is always good :).

---

### Post by RiceMonster on 2010-06-30
> **Simian Man said:**
> You can also do this with nslookup:
```

nslookup www.google.com | tail -n -3 | grep Address

```

But learning new things is always good :).

You can even just get a websites IP with ping.

---

### Post by sxmaxchine on 2010-06-30
I understand that you can use ping however there are many people (especially windows users) who dont know how to use ping.

And im sure there are many programs that can do what my program does but i am currently working on a gui. I want it to be easy to use for anyone because i like simple easy to learn things.

---

### Post by donkyhotay on 2010-06-30
Looks like a good start, as mentioned previously there are already other methods of getting the IP address of a website however even if no one ever uses your program you will have learned something and others can study your code as well.

---

### Post by phrostbyte on 2010-06-30
Very good start. :)

---

### Post by sxmaxchine on 2010-06-30
Thanks for the comments also have any of you used it successfully on ubuntu because i want it to work on ubuntu.
I havent tested because my pc is broken.

---

### Post by wkhasintha on 2010-06-30
great. :)

---

### Post by Frogs Hair on 2010-06-30
I am interested in your project because I have a hard time trying to find the stream IP for radio stations . Some stations post them on the web others do not and I'd like to add more stations  to Rhythm Box. There are Windows programs that do this, most have data collection adware.  I have not found a program for Linux yet and I would like to use Rhythm Box rather than listen via the web browser.

---

### Post by whiskeylover on 2010-06-30
> **Frogs Hair said:**
> I am interested in your project because I have a hard time trying to find the stream IP for radio stations . Some stations post them on the web others do not and I'd like to add more stations  to Rhythm Box. There are Windows programs that do this, most have data collection adware.  I have not found a program for Linux yet and I would like to use Rhythm Box rather than listen via the web browser.

Substituting the domain name with the IP address might not be a good idea in all cases. If the domain is hosted on a shared server, it will have no way of knowing which domain to point your request to, if you don't supply the domain name in the HTTP request.

---

