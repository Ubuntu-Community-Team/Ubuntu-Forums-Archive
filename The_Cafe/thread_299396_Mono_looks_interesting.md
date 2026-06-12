---
title: "Mono looks interesting"
date: 2006-11-14
forum: The Cafe
---

### Post by ade234uk on 2006-11-14
I know some people do not like Mono, but I was looking through Linux Format at one the tutorials and it does look interesting.

What I wanted to know is if Mono is cross platform. If I created something in Mono would it run in Windows & Vice Versa?

---

### Post by gnomeuser on 2006-11-14
Yes, Mono does run on Windows and your code should also be fairly easy to make work with the Microsoft .NET implementation. You will need a little bit to code changes for path handling and such but nothing you could handle conditionally at very low cost.

---

### Post by Wolki on 2006-11-14
It depends on the libraries you use, though. Some of the gnome#-libraries are, as far as I know, not ported to windows yet.

---

### Post by sweemeng on 2006-11-14
mono can be run on windows, but try to get it run with the existing .net framework is a pain. 

unlike visual .net, where windows form can be design visually, mono cannot, but it uses gtk#, on one hand, c# program with windows form run flawlessly, but try to get gtk# running natively like other .net application is a pain. 

but if you are running it on linux, it work very well

---

### Post by chaosgeisterchen on 2006-11-14
If the Windows-Forms-API will be ever copied properly, Mono will become truly a cross-plattform-computing framework.

But the ones forking Windows Forms will be sued my Microsoft...

---

### Post by skymt on 2006-11-14
The brand-new Mono 1.2 is supposed to have a very good Windows Forms implementation.

---

### Post by chaosgeisterchen on 2006-11-14
Isn't Microsoft trying to prohibit that? Or will this vanish with the aggreement between Microsoft and Novell?

---

### Post by Virogenesis on 2006-11-14
if you want cross platform, stick to java now its GPL its only going to get better and better.

---

### Post by chaosgeisterchen on 2006-11-14
> **Virogenesis said:**
> if you want cross platform, stick to java now its GPL its only going to get better and better.

And what about terms of performance? Ain't Mono doing better concerning performance?

---

### Post by skymt on 2006-11-14
> **chaosgeisterchen said:**
> Isn't Microsoft trying to prohibit that? Or will this vanish with the aggreement between Microsoft and Novell?

I think Novell mostly made the MS deal so they could keep Forms in Mono. I'm not sure (very few people have seen the actual text of the agreement), but that's what my intuition tells me.

---

### Post by chaosgeisterchen on 2006-11-14
> **skymt said:**
> I think Novell mostly made the MS deal so they could keep Forms in Mono. I'm not sure (very few people have seen the actual text of the agreement), but that's what my intuition tells me.

Sounds reasonable and I can seond your thoughts. They get Forms in Mono and a 300 million money present.

---

