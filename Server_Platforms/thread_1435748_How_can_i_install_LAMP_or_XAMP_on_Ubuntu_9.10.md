---
title: "How can i install LAMP or XAMP on Ubuntu 9.10"
date: 2010-03-21
forum: Server Platforms
---

### Post by Edgar09 on 2010-03-21
Hello Everyone.
I am having trouble trying to install LAMP or XAMP
I just cant get the whole process done right.
I always get an error..
Can any one help me out cause i feel iam still a newbie.
thanks
;)

---

### Post by Ryan Dwyer on 2010-03-21
sudo apt-get install apache2 libapache2-mod-php5 php5-mysql mysql-server

---

### Post by FuturePilot on 2010-03-21
```
sudo tasksel
```
Hilight the option for LAMP, then press the spacebar to check it. Then press the Enter key and it will do its magic.

---

### Post by dudumomo on 2010-03-22
I used tasksel as well.
Very useful.
Then I've read a couple a tutorial about how to config it. 

Now I've done my own and clear (I hope) tutorial on my blog.

---

### Post by dazz100 on 2010-05-01
Hi

I have done a fresh install of 9.10.
Tried both apt-get and tasksel.  Neither worked.
apt-get couldn't find psp5 and tasksel menu did not include lamp.
I also tried the "Ubuntu Software Centre".  No joy.

Any suggestions??

---

### Post by Edgar09 on 2010-05-01
> **dazz100 said:**
> Hi

I have done a fresh install of 9.10.
Tried both apt-get and tasksel.  Neither worked.
apt-get couldn't find psp5 and tasksel menu did not include lamp.
I also tried the "Ubuntu Software Centre".  No joy.

Any suggestions??
O.k dude i found a video(tutorial) which helped me alot on how to install xampp 

[http://www.youtube.com/watch?v=91Kn30wWyOI](http://www.youtube.com/watch?v=91Kn30wWyOI)

With this you will have the power on php,mySQL!
Trust Me 
xD

---

### Post by Edgar09 on 2010-05-01
> **dazz100 said:**
> Hi

I have done a fresh install of 9.10.
Tried both apt-get and tasksel.  Neither worked.
apt-get couldn't find psp5 and tasksel menu did not include lamp.
I also tried the "Ubuntu Software Centre".  No joy.

Any suggestions??
O.k dude i found a video(tutorial) which helped me alot on how to install xampp 

[http://www.youtube.com/watch?v=91Kn30wWyOI](http://www.youtube.com/watch?v=91Kn30wWyOI)

With this you will have the power on php,mySQL!
Trust Me 
xD

---

### Post by Ryan Dwyer on 2010-05-01
I highly advise you don't follow the instructions in that video, for many reasons.

- The software is downloaded from a third party website then run with root permissions. You're blindly trusting that the software doesn't contain any malware, which is a very bad idea.
- The software isn't installed using the package system, so Ubuntu doesn't know that you have Apache or MySQL installed. If you try to install something that uses Apache or MySQL, it will fail.
- The software will not be kept up to date with security patches, which may eventually lead to your system being compromised.
- This method is slower than all the methods suggested above.

Is there any reason why you didn't follow our instructions? Did you have difficulty with them?

---

### Post by Ryan Dwyer on 2010-05-01
> **dazz100 said:**
> Hi

I have done a fresh install of 9.10.
Tried both apt-get and tasksel.  Neither worked.
apt-get couldn't find psp5 and tasksel menu did not include lamp.
I also tried the "Ubuntu Software Centre".  No joy.

Any suggestions??

There are more options in the tasksel menu. You need to scroll down past the bottom one.

And it's php5, not psp5.

---

### Post by dazz100 on 2010-05-01
Something weird happened.
Over the last 24hrs tasksel only gave me about 3 options.  I ran it again just now and it came up with about 20 options. I am now installing LAMP.

---

### Post by Edgar09 on 2010-05-02
> **Ryan Dwyer said:**
> I highly advise you don't follow the instructions in that video, for many reasons.

- The software is downloaded from a third party website then run with root permissions. You're blindly trusting that the software doesn't contain any malware, which is a very bad idea.
- The software isn't installed using the package system, so Ubuntu doesn't know that you have Apache or MySQL installed. If you try to install something that uses Apache or MySQL, it will fail.
- The software will not be kept up to date with security patches, which may eventually lead to your system being compromised.
- This method is slower than all the methods suggested above.

Is there any reason why you didn't follow our instructions? Did you have difficulty with them?
i download it from the xampp home page
And it works fine...
I would advise to try it our first and test on it if there are any failures
=)

---

### Post by Edgar09 on 2010-05-02
> **Ryan Dwyer said:**
> I highly advise you don't follow the instructions in that video, for many reasons.

- The software is downloaded from a third party website then run with root permissions. You're blindly trusting that the software doesn't contain any malware, which is a very bad idea.
- The software isn't installed using the package system, so Ubuntu doesn't know that you have Apache or MySQL installed. If you try to install something that uses Apache or MySQL, it will fail.
- The software will not be kept up to date with security patches, which may eventually lead to your system being compromised.
- This method is slower than all the methods suggested above.

Is there any reason why you didn't follow our instructions? Did you have difficulty with them?
i download it from the xampp home page
And it works fine...
I would advise to try it our first and test on it if there are any failures:popcorn:
=)

---

### Post by krodrigue on 2010-05-05
apt-get install lamp-server^

That should install everything, then just add phpmyadmin.

---

### Post by ozstar on 2010-06-23
HI,

I did the tasksel as previously mentioned and then cranked up FireFox with localhost in the url and got the message..It Works!  This is the default web page for this server but no content is added.

I looked but am not sure where do I add my web pages?

Thanks

oz

---

### Post by Ryan Dwyer on 2010-06-23
In /var/www. You'll need to use sudo to change files in that directory.

---

