---
title: "Assistance With Virtualbox"
date: 2012-03-13
forum: Virtualisation
---

### Post by zehfofinhu on 2012-03-13
Hi everyone... 

Taking advantage of this openned topic ... 

I&#7743; having some troubles with virtual box ... 

My OS is UBUNTU 11.1, and I emulated on this a Win 7 OS.

I just had emulated Win 7 to make AUTOCAD 2007 and 2012 works properlly.
With AutoCad everything OK, my problem started when I tried to install SOLIDWORKS 2011 on this emulated Win 7.

A message with "cannot open, pelase verify if you had permission to do this" but I had this permission, AUTOCAD and OFFICE 2010 are already instaled ... 

Can anyone help me with this instal ... 
Or 
Help me with install this software directly on UBUNTU without emulated WIN 7 ...

Thanks everyone ... 

I couldn't find the link to create a new TOPIC thats why I'm writing here ... 
This topic is on the same line of my doubt.

---

### Post by Old_Grey_Wolf on 2012-03-13
> **zehfofinhu said:**
> Hi everyone... 

Taking advantage of this openned topic ... 

I&#7743; having some troubles with virtual box ... 

My OS is UBUNTU 11.1, and I emulated on this a Win 7 OS.

I just had emulated Win 7 to make AUTOCAD 2007 and 2012 works properlly.
With AutoCad everything OK, my problem started when I tried to install SOLIDWORKS 2011 on this emulated Win 7.

A message with "cannot open, pelase verify if you had permission to do this" but I had this permission, AUTOCAD and OFFICE 2010 are already instaled ... 

Can anyone help me with this instal ... 
Or 
Help me with install this software directly on UBUNTU without emulated WIN 7 ...

Thanks everyone ... 

I couldn't find the link to create a new TOPIC thats why I'm writing here ... 
This topic is on the same line of my doubt.

You should start you own tread for this problem.

Are you saying that you have Ubuntu 11.10 as the Host OS with Virtualbox running a Windows 7 VM? Are you saying that you can not install SOLIDWORKS 2011 on the Windows 7 guest VM?

---

### Post by howefield on 2012-03-14
> **zehfofinhu said:**
> Hi everyone... 

Taking advantage of this openned topic ....

How rude.

Posts split off to own thread.

---

### Post by zehfofinhu on 2012-03-14
Hi everyone ... 

Sorry about my rude action yesterday ... 
and Thanks to moving my question to new Thread, I&#7743; really glad.

---

### Post by zehfofinhu on 2012-03-14
> **Old_Gray_Wolf said:**
> You should start you own tread for this problem.

Are you saying that you have Ubuntu 11.10 as the Host OS with Virtualbox running a Windows 7 VM? Are you saying that you can not install SOLIDWORKS 2011 on the Windows 7 guest VM?

Yes ... this is exactly my problem ... 
SOLID WORKS 2011 doesn't install on Windows 7 guest VM.

Other heavy aplications are runing OK
Aplications like AutoCad 2007, and MS Office 2010.
Theese two aplications are running faster on Windows 7 VM then on windows 7 instaled directly on HDD. 

But solid works nothing ... 

Before I use VM I had tried to install AutoCad and SolidWorks by WINE and PLAYONLINUX but I didn't have sucess ... 

Thanks everyone ... 

Sorry by my english it it sounds bad very often ... I&#7743; little rusty in this language ... lol

---

### Post by Old_Grey_Wolf on 2012-03-14
zehfofinhu,

Please post the exact error message you got when installing SOLIDWORKS 2011. The error "cannot open, pelase verify if you had permission to do this" does not produce any results when I search for it.

I think it is probably a Microsoft Windows installer error; however, I can't be sure without the exact message you are getting.

Since it doesn't appear to be an Ubuntu error or a VirtualBox error, you may get better response from a Microsoft Windows or the SolidWorks website.

---

### Post by Old_Grey_Wolf on 2012-03-14
> **howefield said:**
> How rude.

Posts split off to own thread.

howefield,

Can you post a link to the new thread? I can't find it :redface:

---

### Post by MSPdwalt on 2012-03-14
That's a windows problem dude, but I'll try and help anyway. (Windows admin by day)

1. are you running 32-bit or 64-bit?
2. based on question 1 are you using the correct installer?
3. Do you have the vbox tools installed on the Guest VM? (more familiar with vmware than vbox so I'm not exactly sure what they're called)
4. Does your VM meet the minimum system requirements for solidworks?
5. Choose the option to run it as an administrator.

---

### Post by zehfofinhu on 2012-03-14
> **Old_Gray_Wolf said:**
> zehfofinhu,

Please post the exact error message you got when installing SOLIDWORKS 2011. The error "cannot open, pelase verify if you had permission to do this" does not produce any results when I search for it.

I think it is probably a Microsoft Windows installer error; however, I can't be sure without the exact message you are getting.

Since it doesn't appear to be an Ubuntu error or a VirtualBox error, you may get better response from a Microsoft Windows or the SolidWorks website.

Hi ... 
I&#7743; not at my notebook at this moment ... tomorrow I will copy the exactly erro message and I will post it here.
But ... I can tell you ... I have already use this installer at Win7 installed directly on HD and it works ... and it is my big trouble ... 

Thanks for answering ...

---

### Post by zehfofinhu on 2012-03-14
> **MSPdwalt said:**
> That's a windows problem dude, but I'll try and help anyway. (Windows admin by day)

1. are you running 32-bit or 64-bit?
2. based on question 1 are you using the correct installer?
3. Do you have the vbox tools installed on the Guest VM? (more familiar with vmware than vbox so I'm not exactly sure what they're called)
4. Does your VM meet the minimum system requirements for solidworks?
5. Choose the option to run it as an administrator.

Hi ... 
For a linux user ... answer Windows questions should be very boring lol ... 

1 - My system is 32-bit.
2 - Yes, I&#7743; using a 32-bit installer, by the way, this installer is 32-bit and 64-bit.
3 - Yes ... I have already installed this tools to make my video driver works properly.
4 - Yes ... my VM meet the minimum requirements of RAM HD, other software requirements usually are installed by the SOLIDWORKS INSTALLER during the installation.
5 - Yes ... I done this. 
And I tried to run im compatibility mode too ... 

Thanks for your help.

See you

---

### Post by MSPdwalt on 2012-03-14
Make sure you're using the proprietary (restricted) graphics drivers on ubuntu and they're up to date.

Are your CPU virtualization extensions enabled in the BIOS? (intel calls their's VT technology and I forget what AMD's are)

Where are you running this installer from? Desktop? network share? C: drive?

Open a windows explorer window, go to tools > folder options > view tab and scroll all the way to the bottom and un-check use simple file sharing.  Then right-click on your Solidworks installer, go to proprieties  and look at the security tab.  Make sure your user has full control.

If your user has full control your installer must have been corrupted somehow.  If you've paid for solidworks (not judging if it's pirated) their support is really good, just don't tell them you're running it on a vm, it's probably not supported.

---

### Post by zehfofinhu on 2012-03-14
> **Old_Gray_Wolf said:**
> howefield,

Can you post a link to the new thread? I can't find it :redface:

Hi ... the first time I accessed the forum ... this option wasn't clear for me too ... 

But since the second time I had accessed it ... this option is showed to me at the first line before the threads already created ... 

Thanks ... 
See you ...

---

### Post by Old_Grey_Wolf on 2012-03-15
You need to provide MSPdwalt with answers to his questions.

Because you hijacked wisdomlight's thread, I didn't know if you followed all the instructions given to him/her or not. I also was not sure you were having the same problem; however, it appears now that you were not having the same problem.

____________________________
> **zehfofinhu said:**
> Hi ... the first time I accessed the forum ... this option wasn't clear for me too ... 

But since the second time I had accessed it ... this option is showed to me at the first line before the threads already created ... 


I never left the thread. I left it open in a tab. It was split off as its own thread while I was still in it; therefore, I didn't see it was split off until I exited the thread and came back later. I've been using the forum for years and I have seen some things happen like that several times. It is not anything for me to worry about nor care about actually.

---

### Post by zehfofinhu on 2012-03-16
Hi ...Old_Gray_wolf ... 

Ok ... 
But I didn't understand, you looks like to me little "angry" ... 

I never say you left the thread ... 
I just answer your comment with waht happened to me ... wasn't my wish make anyone angry ... 


And about tips of MSPdwalt ... I will try to do it now ... 

Thanks and sorry by my mistake
See you

---

### Post by zehfofinhu on 2012-03-16
> **Old_Gray_Wolf said:**
> zehfofinhu,

Please post the exact error message you got when installing SOLIDWORKS 2011. The error "cannot open, pelase verify if you had permission to do this" does not produce any results when I search for it.

I think it is probably a Microsoft Windows installer error; however, I can't be sure without the exact message you are getting.

Since it doesn't appear to be an Ubuntu error or a VirtualBox error, you may get better response from a Microsoft Windows or the SolidWorks website.

Hi again ... 

The exactly problem is on picture under. 

[[IMG]http://img839.imageshack.us/img839/3909/errosolid.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/839/errosolid.jpg/")

Thanks 
See you 

[IMG]http://imageshack.us/photo/my-images/839/errosolid.jpg/[/IMG]
[IMG]http://imageshack.us/photo/my-images/839/errosolid.jpg/[/IMG]

---

### Post by zehfofinhu on 2012-03-16
> **MSPdwalt said:**
> Make sure you're using the proprietary (restricted) graphics drivers on ubuntu and they're up to date.

Are your CPU virtualization extensions enabled in the BIOS? (intel calls their's VT technology and I forget what AMD's are)

Where are you running this installer from? Desktop? network share? C: drive?

Open a windows explorer window, go to tools > folder options > view tab and scroll all the way to the bottom and un-check use simple file sharing.  Then right-click on your Solidworks installer, go to proprieties  and look at the security tab.  Make sure your user has full control.

If your user has full control your installer must have been corrupted somehow.  If you've paid for solidworks (not judging if it's pirated) their support is really good, just don't tell them you're running it on a vm, it's probably not supported.

Hi ... 

How I verify if extensions are enable at BIOS? 

I&#7743; running installer at DESKTOP. 

I made the alterations at folders like you said ... 

At permissions ... my user has access to al itens, less "special permission" this option is unmarked. 

Corrupted file ... I believe isn't the problem ... because I use the same installer at another PC and was all OK. 

No my software isn't paid. So I can't talk to support.

Thanks 
See you ...

---

### Post by Old_Grey_Wolf on 2012-03-16
> **zehfofinhu said:**
> 
I never say you left the thread ... 
I just answer your comment with waht happened to me ... wasn't my wish make anyone angry ... 


 I wasn't angry. I think we have a slight language problem :)

---

### Post by zehfofinhu on 2012-03-17
> **Old_Gray_Wolf said:**
> I wasn't angry. I think we have a slight language problem :)

Yes problem was this ... 
My english conversation wasn't used a long time ...

---

### Post by BertN45 on 2012-03-17
Did you try to right click the setup program and select "run as administrator" as asked before? You do have a problem with permissions and often it can be solved in this way.

Your problem has nothing to do with Virtualbox, it is a problem with the installer of the program.

---

### Post by zehfofinhu on 2012-03-19
> **BertN45 said:**
> Did you try to right click the setup program and select "run as administrator" as asked before? You do have a problem with permissions and often it can be solved in this way.

Your problem has nothing to do with Virtualbox, it is a problem with the installer of the program.

Hi ... 

Yes ... "run as administrator" was the first thing I tried ... 
I will try to make a new download and run it again ... 
Or 
I will try to install it on WIN 7 PC ... 

Thanks

---

