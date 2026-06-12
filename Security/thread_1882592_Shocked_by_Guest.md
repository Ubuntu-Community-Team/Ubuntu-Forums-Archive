---
title: "Shocked by Guest"
date: 2011-11-17
forum: Security
---

### Post by richh1071 on 2011-11-17
Hi

I am dumb struck, I just fired up my laptop and noticed the remembered login user was "guest" at the login screen. I'd never noticed it before,so I clicked on it. Not only could login and get a desktop, I could browse around the files systems. 

Isn't this the sort of thing MS was doing in the 90's. 

Just had a quick look at the User GUI control and there is no sign of a guest account.

I guess this isn't news to you guy's

But I'm seriously annoyed (that wasn't what I originally typed).

That is a breech of trust isn't it. You would expect a modern OS to behave like that.


So now I've been ranting for 5mins I'm hoping I've installed something that has enabled this....

Here's hoping, I'll be back after some digging.

Cao for now

---

### Post by MG&amp;TL on 2011-11-17
A guest can read and execute, but cannot write. So I think it's fairly safe, dependant on what you're doing.

---

### Post by Elfy on 2011-11-17
I assume you are running the newest version.If you want to remove the guest account it is easily accomplished. 

If this is just a rant then I can move the thread out of support areas.

---

### Post by richh1071 on 2011-11-17
Hi

Thanks for the reply, fair play. If you could let me know how to remove it that would be great and I will have a look for a feedback forum, as I think it is naive to think it is safe to allow any access to the system especially out of the box.

Apologies for the rant.

Rich

---

### Post by CharlesA on 2011-11-17
> **richh1071 said:**
> Hi

Thanks for the reply, fair play. If you could let me know how to remove it that would be great and I will have a look for a feedback forum, as I think it is naive to think it is safe to allow any access to the system especially out of the box.

Apologies for the rant.

Rich
Check here:
[http://linuxbsdos.com/ask/2011/10/disable-guest-account-in-ubuntu-11-10/](http://linuxbsdos.com/ask/2011/10/disable-guest-account-in-ubuntu-11-10/)

To see how to disable the guest account.

---

### Post by Elfy on 2011-11-17
Rants are ok - as long as they are constructive - unsurprisingly you;re not the first to notice this - have a look in Recurring Discussions - I know there is one there.  The Testimonial forum is available as well. I'll link at the end. 

So I assume you are using the newest version - we can edit the file to remove the guest - but first we'll backup the file we are editing.

Open a terminal - search in the dash for terminal and open it

Run 

```
sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.bak
```

Now run 

```
gksudo gedit /etc/lightdm/lightdm.conf
```

Add this to the end of the file 

```
allow-guest=false
```

Save and close gedit.

When you next login it should be gone.

[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by Elfy on 2011-11-17
> **CharlesA said:**
> Check here:
[http://linuxbsdos.com/ask/2011/10/disable-guest-account-in-ubuntu-11-10/](http://linuxbsdos.com/ask/2011/10/disable-guest-account-in-ubuntu-11-10/)

To see how to disable the guest account.

That's long winded ... ;)

---

### Post by CharlesA on 2011-11-17
> **forestpiskie said:**
> That's long winded ... ;)
I agree. Yours is better. ;)

---

### Post by richh1071 on 2011-11-17
> **MG&TL said:**
> A guest can read and execute, but cannot write. So I think it's fairly safe, dependant on what you're doing.

Execute rings a few bells.

---

### Post by richh1071 on 2011-11-17
Many thanks for everyone's help, worked a treat. 

I'm off to do my families laptops, we are an Ubuntu household :-)

Rich

---

### Post by MG&amp;TL on 2011-11-17
> **richh1071 said:**
> Execute rings a few bells.

Err...so what are you going to do? You have access to utilities, sure. But you can't use root, you can't write to anything, and you can't leave any traces.

But I agree, if you want secure, don't go there.

---

### Post by Elfy on 2011-11-17
Excellent. 

Can you mark the thread solved - Thread Tools.

---

### Post by richh1071 on 2011-11-17
> **MG&TL said:**
> Err...so what are you going to do? You have access to utilities, sure. But you can't use root, you can't write to anything, and you can't leave any traces.

But I agree, if you want secure, don't go there.

Assuming code is perfect and the bad guys have no talent or imagination.

Anyway, I'm sorted.

Cheers.

---

### Post by F.G. on 2011-11-18
hi richh1071,

i just thought that i'd quickly point out the 'physical access is root access' thing in ubuntu. 

if you're not already aware of it, this means that you can actually boot into recovery mode, choose 'root with command line' or whatever it is start into a root shell, and then type 'startx' and find yourself being able to use root with a whole GUI desktop thing without typing in any passwords. from this you can read, write, install, do whatever you want.

given the nature of this thread i though if you didn't already know, you might want to know this.

i should point out that this is a feature, rather than a fault (in fact an acknowledgement that if you're there physically with the computer, there are easy ways to do all this stuff anyway).

---

### Post by MG&amp;TL on 2011-11-18
> **F.G. said:**
> hi richh1071,

i just thought that i'd quickly point out the 'physical access is root access' thing in ubuntu. 

if you're not already aware of it, this means that you can actually boot into recovery mode, choose 'root with command line' or whatever it is start into a root shell, and then type 'startx' and find yourself being able to use root with a whole GUI desktop thing without typing in any passwords. from this you can read, write, install, do whatever you want.

given the nature of this thread i though if you didn't already know, you might want to know this.

i should point out that this is a feature, rather than a fault (in fact an acknowledgement that if you're there physically with the computer, there are easy ways to do all this stuff anyway).

Or just boot a USB and steal all the files. Or remove the harddrive. Basically, if someone can get at your computer, you're screwed anyway.

---

### Post by F.G. on 2011-11-18
> **MG&TL said:**
> Or just boot a USB and steal all the files. Or remove the harddrive. Basically, if someone can get at your computer, you're screwed anyway.

pretty much. 

in fact i think just recently someone cracked the 'secure boot' mechanism on Windows 8, to try and prevent you from booting from a random bootable medium

---

### Post by richh1071 on 2011-11-18
I guess you don't encrypt your hard drive then. 

For people who seem to know something about security, do you really think it is ok to allow guest access of any kind out of the box?

I guess the point is I left the laptop on and one of my kids had logged on and god know what sites they were clicking away on. I know there is no write access but that;s what malware is all  about isn't it.

The point is if the option isn't there it can't be exploited. 

Secure boot sucks and shows the power of MS, hopefully the Free Software Foundation can kick its ***, show your disdain here..

[http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement](http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement)

---

### Post by emiller12345 on 2011-11-18
So, not that you had this set up like this, but it's possible to have the guest account enabled && have more security.

DEFCON 18: Pwned By The Owner: What Happens When You Steal a Hacker's Computer 1/2
[http://www.youtube.com/watch?v=OAI8S2houW4](http://www.youtube.com/watch?v=OAI8S2houW4)

DEFCON 18: Pwned By The Owner: What Happens When You Steal a Hacker's Computer 2/2
[http://www.youtube.com/watch?v=PSTFP6BYXAE](http://www.youtube.com/watch?v=PSTFP6BYXAE)

using a software package called prey

---

### Post by richh1071 on 2011-11-19
Awesome video, great story.

So, secure your system and data but never recover or have a chance of recovering your kit but data is open. 

I guess you could dual boot your pc with the default OS booting to a set-up rigged to phone home and remote access etc (as per the video) and the other being your system and encrypted.

Still, in my opinion, my original point stands.

---

