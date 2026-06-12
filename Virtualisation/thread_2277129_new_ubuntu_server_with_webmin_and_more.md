---
title: "new ubuntu server with webmin and more"
date: 2015-05-06
forum: Virtualisation
---

### Post by vlad24 on 2015-05-06
Ok, I have been trying to get some help and info forever and finally figure out that this might be the best place to get it.
I have several questions regarding my new build. 
Here we go:
1. I plan to build a server on ubuntu 14.04 or 14.10 server edition with webmin.
I want to use it as a file server (nas) with a single btrfs pool.  And also use it as a virtualization server.

A.   Pleas advice: KVM or XEN
B.   Do I need virtualmin or cloudmin to create and manage VMs on the server.

Again I am installing webmin to manage the server.

---

### Post by TheFu on 2015-05-07
No, you do not need virtualmin or cloudmin.

Do not use btrfs on the host machine. There are warnings against doing this in the KVM performance tuning guides.

---

### Post by vlad24 on 2015-05-07
thanks TheFu, however, I still will be using btrfs for my storage pool as small performance loss is not too important for me.
this is a home server for at most 5 PC and 5 VMs. no biggie.

as for [COLOR=#000000]needing  virtualmin or cloudmin. I know I do not NEED them, but my questions is more which one should I use not which one I need.

[/COLOR]I have read most documents on both and I am still confuse which one do what, hence the question.
if my plan is to have a headless server managed with webmin (I really do hate CLI so plan to use webmin GUI as much as possible)  that will be my VM HOST system, what do I use to manage/administer VMs?
can I use Virtualmin? or I must use Cloudmin for that?  which one is better?

should I use KVM?  or Xen is better? 

that kind of things I am trying to figure out.

I have read losts of posts and forums but many of them do not provide the info I am seeking 
or they are pushing me into opposite directions. like for every post I find PRO-KVM I find an equally valid argument PRO-XEN
how can I choose what is best

---

### Post by TheFu on 2015-05-07
Someone went to the effort to say that btrfs is bad when used for virtual machines. I would listen. 

I've never used either of those virtu-tools - and I think it would be a waste to bother in a small installation. virsh and virt-manage do everything I've ever needed. But I've only been doing virtualization since about 1998, so what do I know? ;)

I don't use webmin.  Linux server management is through the CLI, my scripts or ansible. There are many reasons for this.

KVM or Xen - which is better?  Which color is better - green or blue? They have different use cases and some overlap. What do you plan to do?

The only way to decide these questions is to try everything for yourself.  Nobody else will have similar decision points that match to yours.

---

### Post by vlad24 on 2015-05-07
Thfu, although I do appreciate your opinion and respect your experience in the matter,  I do wonder why do you bother answering this thread if you can not will not offer a constructive answer.  
1. I am asking an opinion on what to use KVM or XEN because KVM have been getting a lot of buz lately and I wonder if it is a viable option compared to xen. I of course understand that we all have our preferences but never heart to ask.

As for using cli only option for managing linux server, well again it is your choice,  I prefer gui.

---

### Post by Tadaen_Sylvermane on 2015-05-17
I don't know what webmin does but you should learn some command line. If something breaks no GUI will help that. I suggest KVM managed with kimchi. CLI KVM is definitely not user friendly.

---

### Post by KillerKelvUK on 2015-05-18
Personal preference is KVM, I tried Xen way back (granted I was full noob then, now only part noob) and had issues with EFI hosts and debugging.  I've so far come across zero problems with KVM that I couldn't either resolve myself (google) or the community here couldn't answer.  ThFu's kinda got a point, the applications are so far reaching every use case could be different and therefore your choice isn't easily addressed.  That said I use KVM for a SoHo and have excellent Win7 performance for my corp stuff (email, visio etc) and I've been able to get VGA and DVB passthrough working with VFIO as well.  Nothing here that Xen can't do although I'd stake that Xen is more difficult to grasp and configure.

For tooling I use CLI (virsh) and Virt-Manager, there are some other web-based (addons) similar to webmin/virtualmin etc (see [http://www.linux-kvm.org/page/Management_Tools](http://www.linux-kvm.org/page/Management_Tools))...I say addons as I've thus far never located a GUI tool that can replace the CLI i.e. the GUI provides 80% if the functionality but if you're in the 20% zone you have no other options that CLI.  Hence heed the feedback from the guys here on this, I doubt you could avoid this forever.

Never used btrfs, maybe I'm ancient or poorly designed...I have a raid 6 DAS using ext4 which is served to clients using samba (win & linux and the linux boxes have some hinky permissions that make NFS more of a challenge for me), high disk IO perf isn't important to me.

---

