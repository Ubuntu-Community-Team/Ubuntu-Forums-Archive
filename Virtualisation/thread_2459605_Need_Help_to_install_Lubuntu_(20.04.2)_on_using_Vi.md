---
title: "Need Help to install Lubuntu (20.04.2) on using Virtualbox 6.1.18"
date: 2021-03-22
forum: Virtualisation
---

### Post by learnlinuxnow on 2021-03-22
**Hello Ubuntu Forum!**

I want and need to Install a form of Ubuntu on my:
 [I][B]
Thinkpad X280
Intel core i-5 8250U
8gb ram

[/B][/I]I need Ubuntu/Xubuntu/Lubuntu cause i follow "the Odin Project" and I want to learn Programming.
I just want to learn all the things running in the background and try to understand them,

([https://www.theodinproject.com/courses/foundations/lessons/prerequisites](https://www.theodinproject.com/courses/foundations/lessons/prerequisites)) [COLOR=#ff0000]<-----That was the guide I used the first time with Ubuntu that worked, but was to slow![/COLOR]
[https://www.youtube.com/watch?v=RxmGFsaOyks](https://www.youtube.com/watch?v=RxmGFsaOyks) [COLOR=#ff0000]<---- This Video also helped me the first time to install guest-additions and a working fullscreen![/COLOR][I][B][COLOR=#ff0000]
[/COLOR]
[/B][/I]Whether what I have done in the end I cant install the guest-additions so that they are working.
I have a really hard time to get my hands on Linux because of this.
[B][I]
What i have tried so far?
[/I][/B]
Ubuntu was the only distro that I could install the guest additions right, but I think my Thinkpad is to slow to use Full-Ubuntu.
Then I tried ZorinOS, LXLE, Xubuntu, Lubuntu and with all them i had problems with installing the guest-additions and they were all very slow i mean like so slow that I cant work with it!

Also i tried using Vmware but it doesnt make any difference!
[B][I]
Are u still reading?

[/I][/B]Then may u could read and go down the rabbit-hole i had a longer friendly conversation on reddit with Paddy Landau, I think he is also in this Forum.
He really helped me with a lot of of things yesterday and it's a long thread with a lot of commands but in the end i dont have fullscreen sadly and i cant use it like that.As a Noob i cant get my head around it, how could it be that it is so hard!

But for all interesting in more details can visit this link [https://www.reddit.com/r/KeePass/comments/m9xbjf/how_to_import_database_from_keepassxc_to_a_vm/](https://www.reddit.com/r/KeePass/comments/m9xbjf/how_to_import_database_from_keepassxc_to_a_vm/).
Cause its complicated to describe all commands i typed!

---

### Post by slickymaster on 2021-03-22
Thread moved to **Virtualisation** for a better fit

---

### Post by TheFu on 2021-03-22
I have a laptop with this same setup, but using KVM as the hypervisor with virt-manager.  It is very fast, including running VMs.
> Intel core i5 8250U
8gb ram

If your VMs aren't getting about 90% of native performance, then something isn't setup right.  With a better hypervisor, say KVM, we can get 95% native performance for everything that isn't a GUI. GUIs always struggle inside VMs.  While not for the exact version of vbox you have, this article will cover the main performance tuning needs: [https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)  The major ideas are all still valid for every hypervisor. The comments explain some stuff too. If you are new, only have 1 hypervisor installed on a system at a time to prevent conflicts.

To learn RoR or whatever the Javascript stuff is they teach, you don't need any specific flavor of Ubuntu or any specific Linux. Pick whatever you like. There are how-to guides for setting up the development environments for all the popular distros.  I learned RoR development and TTD on Ubuntu about a decade ago.  Afterward, I ended up running back to Perl for a number of reasons - mainly stability of the APIs and libraries.  Has RoR stopped repaving the language and Rails every other year yet?  

And don't get me started about Javascript.

As a software developer, you'll need to learn to use man pages. Every command on your system has a manpage that spells out what the command does, all the options available, what each option does, and a few caveats.  Some manpages are small, others are works of art - really impressive.

---

### Post by learnlinuxnow on 2021-03-22
Thank you im sorry i have chosen the wrong part of the forum!

---

### Post by learnlinuxnow on 2021-03-22
Thanks!
 i will go through this and hope i get this working.
First have to learn what a hypervisor is an go through the blog you linked me.
I think they have not stopped to update the rails part but you can choose at one point if you want to go for javascript and node or net or Rails.

Yes i have to learn to read documentation at first, but i have gone nuts why i cant install the guest-additions on Linux. 
Without fullscreen i cant do anything on my VM.

---

### Post by CelticWarrior on 2021-03-22
Virtualbox is an hypervisor. There are many other.

In any Ubuntu you can install the guest additions directly by the Ubuntu repository, no need to use the script provided by the "insert guest additions...".

---

### Post by ActionParsnip on 2021-03-22
Why do you need guest additions?

---

### Post by learnlinuxnow on 2021-03-22
> **CelticWarrior said:**
> Virtualbox is an hypervisor. There are many other.

In any Ubuntu you can install the guest additions directly by the Ubuntu repository, no need to use the script provided by the "insert guest additions...".

i didn't know that, how would i do that can you explain it or prove me with a link!
Thanks!

---

### Post by learnlinuxnow on 2021-03-22
> **ActionParsnip said:**
> Why do you need guest additions?

Cause i dont have  fullscreen!

---

### Post by learnlinuxnow on 2021-03-23
**Update!**

I installed vmware and Lubuntu 20.04.2 cause of vmware's easy installation, guest-additions installed by itself.
I have given the VM 4gb ram and 3 cpu cores they work like a charm!
So finally i can learn Linux :=)

How can i mark the thread as "solved"?

---

### Post by slickymaster on 2021-03-23
> **learnlinuxnow said:**
> ....

How can i mark the thread as "solved"?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by TheFu on 2021-03-23
So much for following the tuning parameters in the link I provided.  3 vCPUs is probably 3x to many.

Only the OP can use the "_Thread Tools_" button to set the thread as SOLVED. Nobody else.

---

