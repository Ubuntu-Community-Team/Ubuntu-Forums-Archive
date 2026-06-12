---
title: "Doing Banking on a PC INFESTED with viruses, Trojans and key-loggers...."
date: 2013-04-30
forum: Security
---

### Post by fatboy123 on 2013-04-30
Hello everyone and thank you for your time, I'm a father of 4 adolescent boys with raging hormones, if they're not watching porn, they're hacking or cracking or doing something immoral, we only have one computer in the house and it's CHOCK full of viruses, Trojans, key-loggers you name it, last year I just gave up trying to scan and clean HUNDREDS of malware daily.

Now my question is, I sometimes need to do some emergency online banking on this computer and I shudder just thinking about the safety factor. I've read some things about a version of LINUX called LPS that I can install on a flash drive, install Firefox on it and use that to boot my PC and do banking safely.

I'm not very experienced and have never used or seen any other OS apart from windows, but a quick learner, all I want in order not to get confused with information overload is just a link or two to get started in the right direction,

What OS should I use?
What Browser should I use?
Should Any firewall or AV be installed on the USB?
Will LastPass work on a USB with Linux?

Any advise highly appreciated.

Bobak.

---

### Post by fatboy123 on 2013-04-30
Here's the link to the LPS I was introduced to...
[http://www.spi.dod.mil/lipose.htm](http://www.spi.dod.mil/lipose.htm)

---

### Post by codemaniac on 2013-04-30
fatboy123,

Welcome to the UbuntuForums!! Your thread is moved to "Security Discussions" subforum.

Ubuntu or Linux in general, is considered more secure than the windows environment.

The below community wiki page can answer most of your queries. 

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

cheers!!

---

### Post by HermanAB on 2013-04-30
You can use any Live Linux CD from Ubuntu, Fedora, Mageia, Suse, Knoppix... and just use it.

---

### Post by gamblor01 on 2013-04-30
> **fatboy123 said:**
> 
What OS should I use?


As others have suggested, any live CD should work just fine.  However, as this is an Ubuntu forum the suggestions you get are likely going to be skewed in its favor.  ;)  I believe that beginning with Ubuntu 13.04 there is no longer any live CD.  You can either burn a bootable DVD or boot from a USB key.  Here is some further info.  See the links on the right side of the page for additional information about creating bootable media:

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

> **fatboy123 said:**
> 
What Browser should I use?


Ubuntu comes with Firefox pre-loaded.  That should be sufficient but feel free to install something else if you want (Chrome, Opera, ...).

> **fatboy123 said:**
> 
Should Any firewall or AV be installed on the USB?


It's not really necessary.  You can if you wish but if you're booting off live media then it's separate and a "clean slate" each time you boot it up.  One neat thing to consider is that you can install AV (such as clam AV) and then mount your Windows partition and scan it.  In this way you can actually scan the Windows partition while running Linux.  Neat huh?

> **fatboy123 said:**
> 
Will LastPass work on a USB with Linux?


Yes.  Another good option is a program called KeePassX.  You can install it by launching a terminal (easiest way is to press CTRL+ALT+T) and then enter this command:

```
sudo apt-get install keepassx
```

It has dependencies on the Qt framework which it should pull in automatically.  If not and it fails stating that it depends on something else, you should be able to get it to install by following it up with this:

```
sudo apt-get install -f
```

---

### Post by fatboy123 on 2013-04-30
Wow thank you so much for answering all my questions.

I will follow these steps tomorrow and make my own USB ...
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

A few more questions if you don't mind:

1- The above link is better for me then the LPS mentioned before? or it makes no difference?
2- So after that I can just boot from that stick using my infected PC and I'll be safe within that USB environment?
3- If I install LastPass and update a password field, will it get saved?
4- If I download something, will it save on the flash itself?
5- Can I use this flash on any hotel, Internet cafe or other unsafe computers?

Thank you so much again.

Bobak.

---

### Post by cool110 on 2013-04-30
1. Ubuntu will probably be easier to use than LPS
2. Yes (But avoid running software from untrusted sources) 
3 and 4. Only if you create a persistence file on the USB
5. Yes

---

### Post by tubbygweilo on 2013-04-30
Bobak,
Just saw this [http://ubuntuforums.org/showthread.php?t=2139675](http://ubuntuforums.org/showthread.php?t=2139675) and thought it might help you with creating a system on a usb stick.

---

### Post by fatboy123 on 2013-05-02
Thank you all so much again, I've spent two days now reading your links and getting to grips with Ubuntu (it's not easy when you're old and senile :)

I installed LPS onto another flash just to test it out, it loads fast on to the desktop but it's not for me as it doesn't remember any settings.

Regarding Ubuntu 13.04, I created a LiveUSB with 1GB persistence, I have another list of questions which I hope will not anger people, I did do a lot of searching and couldn't find answers to them:



1- How do I bypass &#8220;Try it / Install&#8221; screen when booting from USB Live Session? (without installing in the USB), I read somewhere that You can remove ubiquity package but I have no idea how to do that. Google didn't have any answers either.

2- There is a lot of lag, hesitation and some freezing happening, takes a long time to boot too, is this normal or depending on the type of flash stick I'm using (SanDisk Cruzer micro 2GB)

3- I have no ability to right click on the desktop or save something on it, but when I open the file manager and then desktop, I do see files on it. (But not on the actual desktop) is this the normal behavior?

4- When I connect my USB in windows, where do I find my DOCUMENTS folder on the USB so that I can transfer some of my files into it?

5- There is no Log In or password when starting Ubuntu, is this safe? or should I enable log in?

6- Should I enable some other safety feature manually? like firewall or some other important feature which is off by default?

7- I have a docx file inside a 7zip archive which I store all my sensitive information, I can open this directly from within 7zip in windows but could not do that in Ubuntu, I had to first extract it, which is okay but then how do I PERMANENTLY and safely delete that docx file?



I apologize again for wasting your times with all these newbie questions, I assure you that I'm almost there in licking this thing ;)

Bobak.

---

### Post by cool110 on 2013-05-02
1. I wouldn't mess with this
2. Live environments are always slow, using a USB 3 device and port may improve things.
3. You should be able to save the desktop (I just tested in a VM)
4. Windows can't access the contents of the persistence file, files added to the USB by Windows will be accessible as read only in /cdrom
5. If only you have access to the drive you should be fine without a password
6. Unless you are running a server there is no need for a firewall
7. The only way to be sure is to zero out the persistence file to start from a fresh image

---

### Post by ronnyroll on 2013-05-02
you can try mcafee, it is successful with my system. take licensed version and not free one.

---

### Post by fatboy123 on 2013-05-02
.

Thanks again cool110, you've been very kind.  I've noticed Ubuntu is WAY more OS then I need, just to clear things out, here are my exact needs:

1- Very basic fast bootable OS with persistence option.
2- Firefox and Open office which remembers settings and addons.

And that's about it, I just need to do basic banking and shut down, before I try other distros, can someone narrow or add to this list ...


-Damn small Linux
-Puppy Linux
-Debian
-Slax

---

### Post by tubbygweilo on 2013-05-02
An idea to consider. 
Have a look at the partedmagic live cd [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start), I know it is a system disk tool type package but it is light, small, contains a browser and a few tools for fighting with infected or ailing systems. The desktop is simple [http://partedmagic.com/doku.php?id=screenshots](http://partedmagic.com/doku.php?id=screenshots) and a browser [https://en.wikipedia.org/wiki/Parted_Magic](https://en.wikipedia.org/wiki/Parted_Magic), I reckon this contains all you need to run your banking and is way,way smaller than a full fat Ubuntu.

Have a look, cut an .iso and see what you think.

---

