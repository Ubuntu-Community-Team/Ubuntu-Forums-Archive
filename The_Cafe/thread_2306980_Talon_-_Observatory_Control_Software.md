---
title: "Talon - Observatory Control Software"
date: 2015-12-20
forum: The Cafe
---

### Post by doug31 on 2015-12-20
at [http://sourceforge.net/projects/observatory/](http://sourceforge.net/projects/observatory/) there  is a program i would like loaded onto a 1.OTB wd hard drive with ubuntu operating system fully working so i can use the program not learn 

computer programing for the next hundred years 

can someone do it 

<snipped>

---

### Post by Bucky Ball on 2015-12-20
*Thread moved to **The Cafe**.*

---

### Post by ian-weisser on 2015-12-20
It seems in violation of the GPLv2 License it claims to use - no LICENSE file, and archives/binaries without obvious sorce code or where to obtain the source code.

I recommend you find a local linux guru and pay them for their time - it will need to be compiled, adapted to Ubuntu, and debugged. A solid half-day of hard work, if all goes well. Looking at the weird stuff in that tarball, I suspect it may take several days of work before it compiles cleanly.

---

### Post by doug31 on 2015-12-21
thanks for that i do not mind if it is in linux  anyone

---

### Post by matt_symes on 2015-12-21
Hi

> **ian-weisser said:**
> I recommend you find a local linux guru and pay them for their time - it will need to be compiled, adapted to Ubuntu, and debugged. A solid half-day of hard work, if all goes well. Looking at the weird stuff in that tarball, I suspect it may take several days of work before it compiles cleanly.

This is a good point and well worth considering. 

Do you know any Linux savvy people near you ? I assume not but...

...are there any Linux user groups near where you are - where abouts are you based ? There you will find a number of people there who may help you.

You see the problem is not just creating the hard drive for you but it's also the support. 

What happens if I created the hard drive for you and it did not work with your hardware. You would need support. 

It may be possible for me or others to create a bootable hard drive with Linux on it and the software, if it will compile and build, on the bootable hard hard drive. 

But then the question is: do you know Linux ? What desktop environment would you want ? Do you know how to boot from a bootable harddrive ? Would a virtual machine image be a better solution ?

Linux users in your local Linux users group (LUG) would be able to help you with this by talking through the options and they would be... local to you :)

Anyway, on a matter of practicality, the creation of a hard drive image you could copy to the hard drive yourself would be a better solution than carting hard drive around the world; just in case you get an offer of help. Bear in mind that this is an international forum.

There is also the matter of trust. Would be image be safe to use ? Would it contain malware or back doors ?

Explain your setup and requirements in detail. Explain your level of experience with the Talon software and Linux in detail. If you can give some indication of where abouts you live then that would also be useful and we may be able to suggest some LUGs within your geographical locale.

Answer the points above then we may be able to give you more specific advice.

Kind regards

---

### Post by doug31 on 2015-12-21
thanks Matt 

linux operators are a little light around here 

I have programmed and wired motec and dec s ecu s for v8 and v12 engines 

i have built a mach 3 run cnc a small mill and wire and programmed the operating system to mill my 3 d drawing designs

i started a plasma cutter the programs computer break out and step drive motors are done just waiting on liner platform and torch height control

i can get around inside computers it dose not come easy to me but i persevere  

i found once i got all the bits talking to each other in practical sense hard drive cloning works for me as my memory last only till the next project 

as i have found there is not one program to master to get all this done i have a word for smart program builders 

[COLOR=#000000]There is also the matter of trust. Would be image be safe to use ? Would it contain malware or back doors ? do not get this one as you log on the www and there at it all the time [/COLOR]

[COLOR=#000000]Explain your level of experience with the Talon software 

[/COLOR]it is free and my research indicates it has great capacity to do what i want how ever I  have not seen it working only screen pictures  who is linux 

i just do not have the capacity to bring the source to screen but i can get around once i get the fundamentals

with the   motion control wins I will work it 

  as the more user friendly platform it can be made the bigger the picture 

regards   df

---

### Post by matt_symes on 2015-12-21
Hi

> **doug31 said:**
> thanks Matt 

linux operators are a little light around here 

They can be. 

Search on the Internet for "Linux User Group". You may be able to find local people to help.

> I have programmed and wired motec and dec s ecu s for v8 and v12 engines 

i have built a mach 3 run cnc a small mill and wire and programmed the operating system to mill my 3 d drawing designs

i started a plasma cutter the programs computer break out and step drive motors are done just waiting on liner platform and torch height control

You just need a 3D printer and you'll have an interesting setup there :)

It doesn't explain why you need the Talon software but with kit like that i assume you're building something interesting.

> i can get around inside computers it dose not come easy to me but i persevere  

i found once i got all the bits talking to each other in practical sense hard drive cloning works for me as my memory last only till the next project 

You sound more like a hardware person than a software person. Most people i've met are either one or the other.

> as i have found there is not one program to master to get all this done i have a word for smart program builders 

Personally i think that multiple specialist  tools are better than one but tastes do differ. 

> *There is also the matter of trust. Would be image be safe to use ? Would it contain malware or back doors ?* 

do not get this one as you log on the www and there at it all the time 

Apart from Browser Javascript and such, I have not downloaded any software from a *source i did not trust* for years; especially not an OS.

> *Explain your level of experience with the Talon software *

it is free and my research indicates it has great capacity to do what i want how ever I  have not seen it working only screen pictures  who is linux 

i just do not have the capacity to bring the source to screen but i can get around once i get the fundamentals

with the motion control wins I will work it 

as the more user friendly platform it can be made the bigger the picture

I see. You have not tried the software but you think it may work for you.

Why do you need a 1Tb hard drive ? That's a big capacity hard drive for one program. A USB3; 8/16 Gb pen stick would hold the OS and the software easily and you could run that as a liveUSB or convert it into a virtual machine image if that was better for you.

Anyway, I'll try and build Talon in my build environment here. If Talon will not build then it's a dead end for you and not worth considering the rest.

I'll post back tomorrow evening UK time how i get on with that.

In the meantime:

> Search on the Internet for "Linux User Group <your town>". You may be able to find local people to help.

as you'll need support.

Kind regards

---

### Post by doug31 on 2015-12-21
thanks Matt 

thank you for the effort 

i am searching for contacts

---

### Post by matt_symes on 2015-12-22
Hi

I had a look at that software for you doug31 and it not going to work.

It's too old. The last modifications on it where in 2003.

> talon_0.85.tgz 	**2003-12-29** 	19.2 MB 	88 weekly downloads 	

This is really, really old in the Linux world.

It wants a 2.2 or a 2.4 series kernel to build with no modification. 

We have moved beyond 2.6, 3.x and the most current kernels are 4.x series kernels. 

The widget toolkit is also ancient and that's where i stopped looking so i expect there's more problems with it.

I'm sorry but Talon is not going to work for you. It's just too old. In fact it's ancient. It would take far too much work to get it running with any newish Ubuntu.

You need to find a newer piece of software that does what you wanted Talon to do.

Kind regards

---

### Post by doug31 on 2015-12-22
Thanks Matt 

great of you to have a look oh it is not just me i spent a few days trying to something even at my level 

it is interesting as i tried www contacts to this and not much joy 

thank you to any one else having a look 

df

---

