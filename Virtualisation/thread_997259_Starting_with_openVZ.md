---
title: "Starting with openVZ"
date: 2008-11-29
forum: Virtualisation
---

### Post by Arukas on 2008-11-29
My experience with VMs, was when I was inside of windows xp.  Now, I am trying to do it from Ubuntu (Hardy).  I read the forum sticky and it said openVZ was faster.  I only got as far as installing it.  And I notice something unexpected.  When my computer boots up, it boots into a "openVZ" kernel.  That was very unexpected.  I'm still reading on how to get it to work.

1) My main concern is uninstalling VM (if i don't like them) and ubuntu crashes.  Is that going to be a problem since they make changes to the boot?

2) Does any other VMs out there do some changes other than install something on you computer?  Its not a problem, but the tutorial I read said nothing of the sorts.

3)  I don't understand all I read about VMware, yet.  I'm going to try KVM next.  Are these VM program a good represenation of what others can do?  Or is there a sacrifice between speed and functionality?

---

### Post by bodhi.zazen on 2008-11-29
It depends on what you are wanting to do exactly with virtualization.

Openvz is typically deployed as a server (No X) and is nothing like anything you have ever used in Windows.

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

OpenVZ is a modified kernel and you will not damage Ubuntu by using it. The guests are all in a few directories ...

See also : [https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ)

If you like, on the OpenVZ site you can find links to "Live" CD with OpenVZ pre-installed and configured. I advise these CD and when you boot the live CD you will get a pop up which will show you how to use OpenVZ :

[http://wiki.openvz.org/Download_live_CD](http://wiki.openvz.org/Download_live_CD)

Personally I like OpenVZ , and if you wish I advise the Centos Live CD (from the above link).

As you are coming from Windows I advise VirtualBox (PUEL edition) or VMWare (Server).

---

### Post by Arukas on 2008-11-29
Thanks for the info on openVZ, I will think I will do that.  Glad to know its not hurting anything, 

I have no clue what "X" is.  

The first computer I used was a commadore64. Computers didn't start doing their own thing until Win95.  I've been using Ubuntu for quite a while.  I've used Suse (which had magical features and don't exsist anymore), I played in Red Hat a little too.
That is briefly my expierence with computers.  Also, I don't mind command lines, as long as I know what the commands are.  

I haven't tried VirtualBox or VMware (server) I'm playing with VMware Workstation.  What so speical about any of them yet, and how it compares with openVZ.  

I'd like to get openVZ to work, because it didn't work at all.  

Thanks

---

### Post by canabal on 2008-11-30
The easiest I have found to get to work has been virtualbox

to install just ```
sudo apt-get install virtualbox-ose
```

The setup is very easy, and can be done completely in a gui for everything basic.

---

### Post by Arukas on 2008-11-30
I did that, but virtualbox doesn't want to work, it says a kernal is missing or something.  Not for sure how to fix that.  It says everything installed fine though, just doesn't want to run.

I been playing with Workstation and got that to work, I was going to try server, but haven't figured out how to put it in yet, seems different thatn workstation.

---

