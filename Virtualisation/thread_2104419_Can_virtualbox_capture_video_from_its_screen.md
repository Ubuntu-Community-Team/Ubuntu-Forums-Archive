---
title: "Can virtualbox capture video from its screen?"
date: 2013-01-13
forum: Virtualisation
---

### Post by GnuKian on 2013-01-13
The following link refers to the ability to capture, a built-in feature of Virtual Box.
[https://www.virtualbox.org/ticket/4766](https://www.virtualbox.org/ticket/4766)

And it's mentioned into the link that the feature as a result of the following packages:
[http://www.virtualbox.org/svn/vbox/trunk/src/VBox/Frontends/VBoxHeadless/VideoCapture/](http://www.virtualbox.org/svn/vbox/trunk/src/VBox/Frontends/VBoxHeadless/VideoCapture/)

So, How does it works? I couldn't find any featur into virtualbox menu to enable this ability!



Extra links:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
[http://askubuntu.com/questions/41478/how-do-i-install-the-closed-source-version-of-virtualbox](http://askubuntu.com/questions/41478/how-do-i-install-the-closed-source-version-of-virtualbox)

---

### Post by GnuKian on 2013-01-13
Doesn't virtualbox capture the video?

---

### Post by GnuKian on 2013-01-14
Angrily UP!

I necessarily need to create a movie fast from my project that is run into vBox! Is it possible by virtual box simply?

> video capturing the guest operating system is already available in [VirtualBox]("https://www.virtualbox.org/wiki/VirtualBox") (in the VBoxHeadless front-end to be precise), but it requires an external component that you need to build yourself.How? a clue, please?

---

### Post by haqking on 2013-01-14
> **GnuKian said:**
> Angrily UP!

I necessarily need to create a movie fast from my project that is run into vBox! Is it possible by virtual box simply or I should capture the host screen?


How? a clue, please?

Angrily ?

be patient, you arent paying anyone.

[http://www.jedi.be/blog/2010/08/30/capturing-the-screen-of-your-virtual-machines-using-x-vnc-rdp-or-native/](http://www.jedi.be/blog/2010/08/30/capturing-the-screen-of-your-virtual-machines-using-x-vnc-rdp-or-native/)

However I just record my VM's from my host with Kazam

---

### Post by GnuKian on 2013-01-14
> **haqking said:**
> Angrily ?

be patient, you arent paying anyone.
you're right!
but when there's not any answer after 2 days ...

> **haqking said:**
>  However I just record my VM's from my host with Kazam
Yes, there's different way to capture: 1. capturing the host 2. capturing in guest
But I should try it by VBox internally, this a part of my project. I should explain the instruction for my teacher.
The teacher gave me this link: [https://www.virtualbox.org/ticket/4766](https://www.virtualbox.org/ticket/4766) !!! and ask me for.

---

### Post by dannyboy79 on 2013-01-14
> **GnuKian said:**
> you're right!
but when there's not any answer after 2 days ....
AND? you could wait a week and not get an answer and still NOT have a right to "demand" a rushed answer or an answer at all. This is a community of volunteers. If you need faster answers you may try out the #ubuntu IRC channel on freenode.net

> **GnuKian said:**
> 
Yes, there's different way to capture: 1. capturing the host 2. capturing in guest
But I should try it by VBox internally, this a part of my project. I should explain the instruction for my teacher.
The teacher gave me this link: [https://www.virtualbox.org/ticket/4766](https://www.virtualbox.org/ticket/4766) !!! and ask me for.I would just use kazzam and copy it from my host OS as most times the VM is already running on limited resources to begin with. Just my 2 cents.

---

### Post by GnuKian on 2013-01-14
> **dannyboy79 said:**
> you could wait a week and not get an answer and still NOT have a right to "demand" a rushed answer or an answer at all.
that's correct. sorry :oops:


>  I would just use kazzam and copy it from my host OS as most times the VM is already running on limited resources to begin with. Just my 2 cents.Thank you for tip (kazzam)
But
I Should follow this link: [https://www.virtualbox.org/ticket/4766](https://www.virtualbox.org/ticket/4766) that is a part of my project! I don't understand it!
as short: I should create a movie via virtual box by its features (this a half part of my project, the second half is running my program into VBox and capturing a video of its performance. Is this odd? oh, No, If you see my teacher, he's more odd!)

My problem is video capturing just by VirtualBox?!

(I couldn't find any help from google during these days)

---

### Post by dannyboy79 on 2013-01-14
hmm, so you're saying part of your project is actually using VB's supposed capability to record the guest OS while it's running. You may have better luck on an IRC channel on freenode.net, probably named VirtualBox or something along those lines. I honestly can't help. I read that ticket a bit but don't understand it either.

---

### Post by haqking on 2013-01-14
> **GnuKian said:**
> that's correct. sorry :oops:


Thank you for tip (kazzam)
But
I Should follow this link: [https://www.virtualbox.org/ticket/4766](https://www.virtualbox.org/ticket/4766) that is a part of my project! I don't understand it!
as short: I should create a movie via virtual box by its features (this a half part of my project, the second half is running my program into VBox and capturing a video of its performance. Is this odd? oh, No, If you see my teacher, he's more odd!)

My problem is video capturing just by VirtualBox?!

(I couldn't find any help from google during these days)

Yes my first post responded to your link which is ffmpeg

If you want to capture witin the VM then use capture software in the VM, such as kazam, etc it is the same thing.

You can record the VM from your host, or record from within the VM with screen capture software of choice

---

### Post by GnuKian on 2013-01-14
> **haqking said:**
> You can record the VM from your host, or record  from within the VM with screen capture software of choice
Thank you for the reply. But I must not use any additional software for capturing, whether inside or outside the vBox

> **dannyboy79 said:**
> hmm, so you're saying part of your project is actually using VB's supposed capability to record the guest OS while it's running. You may have ...
I'm afraid my teacher is fooling me?!! (He's already done it before on the students!)
can really VB capture video by itself?

> **dannyboy79 said:**
> You may have better luck on an IRC channel on  freenode.net, probably named VirtualBox or something along those  lines.
Indeed, I don't know how irc works! (I'm going to learn it now)

> **dannyboy79 said:**
> 
I honestly can't help. I read that ticket a bit but don't understand it either.
and  I also tried to create an account in [https://forums.virtualbox.org](https://forums.virtualbox.org) to  ask them about the ticket but the registration steps was really troublesome (finally couldn't)

---

### Post by haqking on 2013-01-14
> **GnuKian said:**
> Thank you for the reply. But I must not use any additional software for capturing, whether inside or outside the vBox


I'm afraid my teacher is fooling me?!! (He's already done it before on the students!)
can really VB capture video by itself?


Indeed, I don't know how irc works! (I'm going to learn it now)


and  I also tried to create an account in [https://forums.virtualbox.org](https://forums.virtualbox.org) to  ask them about the ticket but the registration steps was really troublesome (finally couldn't)

The ticket makes no sense as the person is asking to record the host from the VM (host is the OS that virtual box is running on)

The reply refers you to ffmpeg.

if the guest OS in the VM is linux then ffmpeg is from the command line of the linux VM.

From within a VM you can take a screenshot however.

To record the session you will need to use a tool such as ffmpeg,kazam etc etc

---

### Post by dannyboy79 on 2013-01-14
> **haqking said:**
> The ticket makes no sense as the person is asking to record the host from the VM (host is the OS that virtual box is running on)

The reply refers you to ffmpeg.

if the guest OS in the VM is linux then ffmpeg is from the command line of the linux VM.

From within a VM you can take a screenshot however.

To record the session you will need to use a tool such as ffmpeg,kazam etc etci think that ticket is meaning the OS being "hosted" in the VM but I could be wrong.

---

### Post by haqking on 2013-01-14
To the OP.

Are you sure your teacher didnt mean vmware ?

in vmware you can usevmware record and play or used to be able to.

If its virtual box then you will need to record within it the same way you would record a desktop in any OS with whatever screen capture software you choose.

Peace

---

### Post by GnuKian on 2013-02-03
Teacher emphasized again on the subject. Without any additional explanation!
If you have a forum account in virtualbox forum or If you're familiar with VBox developers, is it possible that you contact them on `Vbox capturing`?

---

