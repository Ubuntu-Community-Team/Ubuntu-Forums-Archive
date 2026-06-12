---
title: "Develop and Excel in Biometric forms of Passwords (Fingerprints, Iris Scans)"
date: 2008-09-17
forum: Ubuntu Brainstorm
---

### Post by IamReck on 2008-09-17
[[IMG]http://brainstorm.ubuntu.com/idea/13184/image/1/[/IMG]]("http://brainstorm.ubuntu.com/idea/13184/")

I believe that passwords are the thing of the past. Today, at my college (Rochester Institute of Technology), we are required to use "pass phrases," at least 15 digits long with uppercase, lowercase, numbers and symbols in it. They also recommend that we use 3 or 4 of each in random order. 

15 - Digits!? :confused:

Why? As computers get faster and faster, it becomes easier for people to crack your password, take a look at this article, and how fast it takes to crack some of those passwords... 

[http://www.lockdown.co.uk/?pg=combi&s=articles ]("http://www.lockdown.co.uk/?pg=combi&s=articles")

While most people these days are smarter with there passwords, the point is computers will be constantly getting more processing power in the future, and constantly getting cheaper. Eventually, who is to say that everyone has to do something similar that I do at my university? I also can not imagine people using anything above 15-digits, it just becomes too much of a pain in the *** to remember. 

So where does that leave us with regards as to what we can do about our security. What are our options. The commercial industry has successfully been integrating Fingerprint readers into laptop computers for a little over the past year I believe, diddo for USB Fingerprint readers. To my knowledge Facial recognition software is in development, and Iris Scanning is something that I have heard about in military applications but not commercially yet. 

So what is that I want? 

I want Ubuntu, and really GNU/Linux in general to excel in the field of Biometric Security, while that may just mean Fingerprint readers today, my idea is for Ubuntu to fully integrate the technology into all future distributions, make it easy to use, with nice GUI, friendly explanations, and seamlessly integrating with everything, from sudo, to me logging into all my Pidgin accounts at once, and using it with my GPG keys. 

If Ubuntu could become the leader in this field, seamlessly integrating it into all of its applications, and log in screens, I believe that it could become one of the reasons to use Ubuntu as well as a feature that makes it stand out in the Operating System Pack. 

Other Operating Systems have already been doing Fingerprint integration, most notably, in my opinion, Microsoft. On my Laptop, which also Runs Windows Vista, I have to option to set up passwords using my fingerprint reader to log in, just by merely swiping a finger, and use it in more then a few applications. At my fathers workplace, it is now a requirement that employees use Fingerprint readers for all of there passwords, and major companies are now installing fingerprint readers built into there laptops. 

The point? Biometrics are the future. Today it is fingerprints, tomorrow, it could be Iris Scanning to Facial recognition software. What I want is fingerprints to be fully working on Ubuntu with as many applications as possible, and especially with in Firefox. 

As security concerns grow, I believe that this will become more apparent, and the day when Canonical can advertise on its website, “Never remember a password again, Ubuntu has Full Fingerprint...” is the day we really see not only commercial interest in Ubuntu take off, but general interest rise to. 

P.S. - Yes I am aware if ThinkFinger, and some other projects out there, but if you look at the development of these projects, such as ThinkFinger's home page... 

[http://thinkfinger.sourceforge.net/ ]("http://thinkfinger.sourceforge.net/")

...which has not been updated. 

Launch Pad also has a Blueprint, which is designated “Low” Priority. 

[https://blueprints.launchpad.net/ubuntu/+spec/fingerprint-authentication ]("https://blueprints.launchpad.net/ubuntu/+spec/fingerprint-authentication")

One more thing... I know in a way this is a duplicate, there are more then a few ideas out there for fingerprint integration, but this is a call for Ubuntu to really get together on this and excel at it. I believe that it is the future, and that when Ubuntu excels at it, it will truly be something to set itself apart from other operating systems.

---

### Post by gnomeuser on 2008-09-17
[Libfprint](http://www.reactivated.net/fprint/wiki/Libfprint)

There you go, we already developed it - as I recall there is a pam module as well so it should be easy to hook up to gdm.

---

### Post by IamReck on 2008-09-17
Its out there, but it isn't really out there is it?  It has been developed, but it isn't included in packages, and it isn't something that even works with all laptops.  If you look at the history for that specific wiki, it hasn't been worked on in over 30 days...  I am calling for active development, I would like Ubuntu integrate Biometric Security right into the installation, have it completely replace passwords, make it work easily, and make it secure.

---

### Post by gnomeuser on 2008-09-17
> **IamReck said:**
> Its out there, but it isn't really out there is it?  It has been developed, but it isn't included in packages, and it isn't something that even works with all laptops.  If you look at the history for that specific wiki, it hasn't been worked on in over 30 days...  I am calling for active development, I would like Ubuntu integrate Biometric Security right into the installation, have it completely replace passwords, make it work easily, and make it secure.

I know we Fedora people have developers working on integrating and designing the user interactions for this. These are volunteers so sometimes time is an issue, which is not optimal but work is being done.

As things stand, today you have the pam module and the drivers. You should be able to log in using a fingerscanner with a little configuration. Provided naturally that your fingerreader is supported, mine isn't so I have been unable to test this.

One problem we would like to solve would early userspace unlocking encrypted root partitions like this. This however is a harder problem to solve.

We welcome your help, if you have the skills required I would be happy to set you in contact with the right people.

---

