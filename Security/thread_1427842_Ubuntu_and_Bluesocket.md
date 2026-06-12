---
title: "Ubuntu and Bluesocket"
date: 2010-03-12
forum: Security
---

### Post by aaroncoffman on 2010-03-12
To start off I do not have the ability to post in the Networking/Wireless thread. 

I attend DeVry university and in my school they recently rolled out "Bluesocket." Now that they have done this I am not able to access the internet utilizing my ubuntu laptop. 
I am able to connect to the network. 
When I open my web browser I am redirected to the "bluesocket" login page where I am able to successfully log in. The next step to accessing DeVry's internet service is to allow Bluesocket to do a scan using a Java applet. That scan is successful.

The results of the scan inform me that I am not being allowed to access the network resources because I don't have an antivirus or firewall program installed on my computer. I do not wish to have an antivirus or firewall program installed on my laptop to utilize DeVry's network resources. 

My question is what steps do I need to take to bypass/trick bluesocket? 

Any help is greatly appreciated and will be shared with other linux users in my school.

---

### Post by cariboo on 2010-03-12
If you are going to use their network, you should follow the rules.

You have a firewall installed already, Either just open a terminal and type:

```
sudo ufw enable
```

or install GUFW.

This just enables a basic set of firewall rules.

As far as an AV scanner is concerned, I would check with the IT department to see if the program can even detect clamav if it isn't running.

---

### Post by aaroncoffman on 2010-03-12
I can understand your point regarding if I use the network then I should follow the rules but the program can also dictate what I can and can't have on my computer whether it's running or not. When I agreed to the original network rules I don't recall agreeing to them having the ability to say what I can and can't have on my personal computer. 

So because of that I would like to bypass it.

Also thank you for the information regarding the firewall and antivirus!

---

### Post by MHaensel on 2010-04-25
You should not be able to bypass BlueSocket without some heavy-duty hacking.

I currently work at DeVry in Fresno, California. Our IT person assures me Ubuntu, MacOS, and Windows are all supported by BlueSocket. It does require that you have a firewall enabled and antivirus software. I didn't inquire whether the antivirus has to be installed or just running. BlueSocket looks for a certain set of antivirus programs, so it may not be helpful to install at random; your local IT person can tell you which antivirus programs will be recognized.

---

### Post by rookcifer on 2010-04-25
Welcome to the world of Windows: it's so insecure that universities now have to put draconian measures in place like this, which I might add, will fail.  AV software is largely ineffective as many studies prove.

I have seen other people post about this "bluesocket" software before and some have had success by explaining they use Linux.  Others have been told, "sorry, no Linux for you."  Obviously most "system admins" out there have no idea what Linux even is.

So, my advice is go talk to the sys admins and explain the situation.  Good luck.

---

### Post by aaroncoffman on 2010-04-26
> **MHaensel said:**
> You should not be able to bypass BlueSocket without some heavy-duty hacking.

I currently work at DeVry in Fresno, California. Our IT person assures me Ubuntu, MacOS, and Windows are all supported by BlueSocket. It does require that you have a firewall enabled and antivirus software. I didn't inquire whether the antivirus has to be installed or just running. BlueSocket looks for a certain set of antivirus programs, so it may not be helpful to install at random; your local IT person can tell you which antivirus programs will be recognized.
I have no want to do any heavy duty hacking or to use programs DeVry doesn't want me to use on my computer while on their network. But when the help desk calls me and asks me what anti virus is good for Ubuntu I have a problem. Yes thats right, the student help desk for my campus called me and asked me what anti virus can be used at DeVry with Ubuntu. 

I can get into a whole other rant about other student's Windows machines that have all of the required software and none of the "disallowed" software but still cannot use the network, but thats not for this forum. 

So I ask you MHaensel why did DeVry (an educational institution who's roots lie it technology education) not prepare more for students that utilize operating systems other than Windows or even in some cases as I stated a moment ago Windows itself. 

I really enjoy being a student at DeVry but I feel a little.. stifled due to this new policy.

---

### Post by cariboo on 2010-04-26
A better question to ask is who's job is it to teach users how to use their computers properly? I know the school district in my area isn't doing a very good job of it.

Back when I went to Technical school, when the only version of Windows was version 1 and it was pretty unusable, we were taught the basics, including a bit of basic programming, but it was still mostly MS-DOS, and viruses were only prevalent on BBS's. 

For the time the training was quite good, but nowadays, the school system, which should be teaching kids how to operate a computer, are teaching them how use Photoshop and Office, and not really teaching the basics.

I think somewhere along the line, because almost everyone now has access to a computer from a very early age, we assume they know what they are doing, but in reality it's just like anything else, we are left to discover how to use a computer by ourselves, and a lot of what we discover when we are young stays with us forever, whether it is right or wrong.

---

### Post by aaroncoffman on 2010-04-26
> **cariboo907 said:**
> A better question to ask is who's job is it to teach users how to use their computers properly? I know the school district in my area isn't doing a very good job of it.

Back when I went to Technical school, when the only version of Windows was version 1 and it was pretty unusable, we were taught the basics, including a bit of basic programming, but it was still mostly MS-DOS, and viruses were only prevalent on BBS's. 

For the time the training was quite good, but nowadays, the school system, which should be teaching kids how to operate a computer, are teaching them how use Photoshop and Office, and not really teaching the basics.

I think somewhere along the line, because almost everyone now has access to a computer from a very early age, we assume they know what they are doing, but in reality it's just like anything else, we are left to discover how to use a computer by ourselves, and a lot of what we discover when we are young stays with us forever, whether it is right or wrong.

Very insightful.

I know that I learn something new all the time. Many many older computer users wish to learn the basics. But what are the basics these days? Where does one start? 

Most of what I have learned about computer operating systems has been on my own. I don't claim to be a knowledgeable individual in regards to computers but I know what resources to utilize to fix issues I run into.

---

