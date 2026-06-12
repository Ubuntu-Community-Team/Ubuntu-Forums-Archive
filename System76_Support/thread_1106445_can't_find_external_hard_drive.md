---
title: "can't find external hard drive"
date: 2009-03-25
forum: System76 Support
---

### Post by accessys on 2009-03-25
just got my new system 76 laptop with ubuntu 8'10 installed, so far works pretty well  but while it can find all my "stuff" it doesn't detect the verbatim exteral hard drive.

the hard drive is connected via USB port and was made with SUSE linux

thanks
Bob

---

### Post by thomasaaron on 2009-03-26
Verbatim hard drives have been known to have some problems.

[http://www.google.com/search?q=ubuntu+verbatim+hard+drive&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=ubuntu+verbatim+hard+drive&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

> but while it can find all my "stuff" it doesn't detect the verbatim exteral hard drive

I'm not sure what you mean. It finds all your stuff where?

---

### Post by accessys on 2009-03-27
> **thomasaaron said:**
> Verbatim hard drives have been known to have some problems.

[http://www.google.com/search?q=ubuntu+verbatim+hard+drive&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=ubuntu+verbatim+hard+drive&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)



I'm not sure what you mean. It finds all your stuff where?


what I mean is that everything else I have pluged into the computer is detected.  SD cards etc.  only the Verbatim External Hard drive, I cannot find it.  I have tried to manually mount it, and have looked in the file systems and it is not found.

this is a new Pangolin System 76 laptop with 64 bit 8.10 installed natively.

I have been using Linux for 10 years or so and the External hard drive is used regularly on my desktop machine which is running SUSE which finds itt without any problem.

Thanks

Bob

---

### Post by thomasaaron on 2009-03-27
What type of filesystem does it have? Is it ext3? Something else?

What is the model number of the drive?

Will it see the drive if you boot with the drive installed?

---

### Post by accessys on 2009-03-27
> **thomasaaron said:**
> What type of filesystem does it have? Is it ext3? Something else?

What is the model number of the drive?

Will it see the drive if you boot with the drive installed?


file system ext 3
Verbatim model #USB320

It does not see it when booting 


Computer is System 76 Pangolin model PANP4N

thanks
Bob

---

### Post by thomasaaron on 2009-03-27
I'm finding nothing useful about this on the web. Verbatim drives don't seem to be very popular with Ubuntu users.

My best estimation is that Verbatim drives have firmware that clashes with Ubuntu. That doesn't happen with external USB drives very often, but every once in a while we run into such a situation.

---

