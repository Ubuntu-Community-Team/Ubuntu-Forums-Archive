---
title: "Can nmap be detected?"
date: 2009-04-02
forum: The Cafe
---

### Post by InsertNameHere on 2009-04-02
Today someone at school someone wanted me to nmap the school's servers using my laptop (they only have 4000 computers.. tsk tsk) so I did.

Just wondering could the school know that I nmaped their networks, on the remote chance I might get in trouble, I just did a operating system scan on random 2 of the 4000 computers before closing it?

I think the teachers are watching me because once I let slip that if I dd'd the schools central server, I might get on the top of the hacker list ;)

Thanks for all replies

---

### Post by dacorr on 2009-04-02
nmap is a common tool and most firewalls and IDS/IPS systems will detect the scans

depends if the IT staff check the logs particually as a trace of the laptop used will also be left.

Dac

---

### Post by Mehall on 2009-04-02
TBH, worst they will do is block the IP.

---

### Post by binbash on 2009-04-02
What type of scan did you use at nmap?Short answer yes it can be detected, but do not worry about it

---

### Post by InsertNameHere on 2009-04-02
But if there are other people using the same model laptop as I, then will they detect it?

Basically, what level of data can be seen?

nmap -v -O 10.*.*.* was what I used

---

### Post by billgoldberg on 2009-04-02
> **InsertNameHere said:**
> But if there are other people using the same model laptop as I, then will they detect it?

Basically, what level of data can be seen?

nmap -v -O 10.*.*.* was what I used

Here is some "light reading" on the subject:

[http://www.securityfocus.com/infocus/1225](http://www.securityfocus.com/infocus/1225)

Don't worry about it, nmap scans aren't illegal in any country, as far as I am aware.

---

### Post by t0p on 2009-04-02
As you've already been told, nmap scans *can* be detected.  But the program does have ways of muddying the waters.  There is a "decoy" mode, where nmap makes it look like it came from one of several addresses - you supply the addresses, and your "victim" will know only that one of the computers on the list is the guilty party.

Sorry, I can't remember the options needed to do this.  But a look at the man page will certainly enlighten you.  Indeed, if you want to use tools like nmap, you should make it your business to learn how to use it.  Otherwise you may end up on a "hacker list" sooner than you'd like...

---

### Post by dacorr on 2009-04-02
possessing the tools are illegal in the UK, they recently changed the law (Computer Misuse Act 1990)

they would log the MAC which is unique.

academic facilities generally dont have the logging facilites and they are not checked anyway... a system is only as good and secure as the person using it.

Dac

---

### Post by Mehall on 2009-04-02
> **dacorr said:**
> possessing the tools are illegal in the UK, they recently changed the law (Computer Misuse Act 1990)

they would log the MAC which is unique.

academic facilities generally dont have the logging facilites and they are not checked anyway... a system is only as good and secure as the person using it.

Dac

WHAT?

that means EVERYONE using linux pretty much is breaking the law!!

I never knew that!!!

*will be emailing his MP soon*

Oh, and some academic facilities DO have the logs. And as I said, worst they can do is block your IP, but that WILL happen in a lot of them.

---

### Post by billgoldberg on 2009-04-02
> **dacorr said:**
> possessing the tools are illegal in the UK, they recently changed the law (Computer Misuse Act 1990)

they would log the MAC which is unique.

academic facilities generally dont have the logging facilites and they are not checked anyway... a system is only as good and secure as the person using it.

Dac

So pretty much any kind of network "security" tool would be illegal.

That's is stupid, and actually pretty unsafe. It would mean IT guys couldn't check their own stuff to see how secure it is.

---

### Post by Mehall on 2009-04-02
> **billgoldberg said:**
> So pretty much any kind of network "security" tool would be illegal.

That's is stupid, and actually pretty unsafe. It would mean IT guys couldn't check their own stuff to see how secure it is.

Penetration testing is VERY important.

You're telling me that the Backtrack cd I have in my cd wallet is roughly as illegal as the UBCD4WIN one I have?

that's fscked up.

---

### Post by InsertNameHere on 2009-04-02
I'm already on the top 10 potential hackers list (they made it after a kid broke into an administrator account, alot of people in this school has no idea how to use a computer properly).

This is a high school by the way, and from the looks of it, the network admin is not that smart (no offense), the only thing they care about is that the server does not crash.

I plugged my laptop into a classroom Ethernet port, What I am wondering is that if they can see my computer name (which if they do I'm screwed)

Is it illegal in Canada? if not then I'm not breaking the law. and to the person above, pretty much anyone using a computer is breaking the law (piracy).

P.S. I don't care if they block the IP, they aren't static, also I don't think they are allowed to confiscate laptops to check the MAC address (if they do, my entire HDD is encrypted with AES Twofish Serpant 256bit, try breaking into that, as well as a BIOS password).

---

### Post by dacorr on 2009-04-02
> **Mehall said:**
> WHAT?

that means EVERYONE using linux pretty much is breaking the law!!

I never knew that!!!

*will be emailing his MP soon*

Oh, and some academic facilities DO have the logs. And as I said, worst they can do is block your IP, but that WILL happen in a lot of them.

pretty much, but its not exactly enforceable, i think it should be changed to cover the intent of the individual but still thats my opinion.

---

### Post by dacorr on 2009-04-02
> **InsertNameHere said:**
> I'm already on the top 10 potential hackers list (they made it after a kid broke into an administrator account).

This is a high school by the way, and from the looks of it, the network admin is not that smart (no offense), the only thing they care about is that the server does not crash.

I plugged my laptop into a classroom Ethernet port, What I am wondering is that if they can see my computer name (which if they do I'm screwed)

Is it illegal in Canada? if not then I'm not breaking the law. and to the person above, pretty much anyone using a computer is breaking the law (piracy).

P.S. I don't care if they block the IP, they aren't static, also I don't think they are allowed to confiscate laptops to check the MAC address (if they do, my entire HDD is encrypted with AES Twofish Serpant 256bit, try breaking into that, as well as a BIOS password).


That would depend on the schools policies that you may have agreed to when logging on. they may not need to acces the laptop, just detect when its on and see who is using it. UK has a law about encryption keys also, if you fail to provide them you get 2 years jail time.

---

### Post by Mehall on 2009-04-02
> **dacorr said:**
> That would depend on the schools policies that you may have agreed to when logging on. they may not need to acces the laptop, just detect when its on and see who is using it. UK has a law about encryption keys also, if you fail to provide them you get 2 years jail time.

I knew we had sucky cyber-laws, but really -________-

It's like a cyber equiv of the US Patriot Act -________-

---

### Post by InsertNameHere on 2009-04-02
> **dacorr said:**
> That would depend on the schools policies that you may have agreed to when logging on. they may not need to acces the laptop, just detect when its on and see who is using it. UK has a law about encryption keys also, if you fail to provide them you get 2 years jail time.

It is not a school computer, it is my personal laptop, they have no clue when its on since I rarely connect to the school's internet. Most times, it's not connected to anything.

Really... you aren't suppose to have encryption keys now..?
But then again, schools don't exactly have a court order do they..?

---

### Post by dacorr on 2009-04-02
UK laws are quite strict, the US based some of the cyber laws on ours and they have recently adopted some of the DPA act also,

problem with schools is that they do have aceptable use policies amoung others that you agree to when accessing the computers so it depends on what the policies state.


 Canadian laws are quite relaxed for this kind of thing so i would not worry depending on what you have done,

---

### Post by t0p on 2009-04-02
> **dacorr said:**
> UK has a law about encryption keys also, if you fail to provide them you get 2 years jail time.

A dumb-*** law if ever I saw one.

Let's say Mr X, the criminal, has illegal stuff encrypted on his computer.  The police come and grab the machine, then take Mr X in front of a judge to be ordered to provide the key.

Mr X considers what precisely he has on his machine.  If it's just some common-or-garden illegal porn, he can supply the key and pay the fine for his dirty pictures.  But if it's detailed plans of the terrorist campaign he's been waging for the past 5 years, he'll tell the judge to go jump himself, and happily do the 2 year sentence instead of the 12 life sentences he'd get if anyone saw what he'd been up to.

Also, encryption projects like truecrypt and elettra have an option where an encrypted directory contains more than one file.  Use password A and it gives up your secret photos of Britney Spears.  Use password B and out pops your secret photos of little boys.  You can decide which password to supply according to what you're willing to admit to.

---

### Post by InsertNameHere on 2009-04-02
I have plausible deniability (two password thing) on a few file containers, but not system wide.

I do not have swap partitions/page files.

But (this is stupid on my part) I already told anyone who's willing to listen I have it... so it's useless (not saying that it will help out in this case, since as long as they can boot the computer, they can have the MAC)

---

### Post by rhcm123 on 2009-04-02
> **InsertNameHere said:**
> 
I plugged my laptop into a classroom Ethernet port, What I am wondering is that if they can see my computer name (which if they do I'm screwed)


Yes, they probably can. Every time i ssh to my server i see on the logs "login from ussr-laptop.(domain)". Set it to somthing random, like fbi-secret-control-system, then change it when you are done grey hatting.

---

### Post by Jags_FL on 2009-04-02
> **InsertNameHere said:**
> my entire HDD is encrypted with AES Twofish Serpant 256bit

Few side questions, if you can : 
How you encrypt **entire** hard drive & is the OS Ubuntu ? Any performance loss, like HD read/write speed...

Many thanks.

---

### Post by InsertNameHere on 2009-04-02
Encrypted windows using truecrypt (I'm using the windows bootloader)
(I don't think truecrypt supports full disk partitioning from linux anyways).

There are other tools though.

Yes speeds are VERY VERY VERY slow, especially during boot, it is better when I'm not in hidden mode (single layer AES). I think that one of my cores is encrypting and decrypting the whole time I'm using my computer.

Just found something for you
[http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530)

P.S. The speed is dependent on your CPU, since it has to encrypt and decrypt all the time.
I'm on a Core 2 Duo 1.66Ghz

---

### Post by Jags_FL on 2009-04-04
@ InsertNameHere

Many thanks. I'll check the thread you mentioned. - jags

---

