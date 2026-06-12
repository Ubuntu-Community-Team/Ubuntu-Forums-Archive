---
title: "3D Gaming Now Possible With Virtualization"
date: 2008-10-05
forum: Virtualisation
---

### Post by go_beep_yourself on 2008-10-05
It looks like it's only available in OSX right now. Please correct me if I am wrong. It proves the theory of being able to do it is true, and maybe Linux will get it soon, hopefully.

[IMG]http://www.vmware.com/files/images/screens_fusion/f2/video_3dgames_lg.jpg[/IMG]

---

### Post by michaelkahl on 2008-10-05
Isn't vmware working on something like this?  I could be wrong, but I thought they were.

---

### Post by go_beep_yourself on 2008-10-05
That is VMWare. Fusion is the VMWare product for OSX. They have done it, not sure they will ever make it possible for Linux users though.

---

### Post by michaelkahl on 2008-10-05
We can hope, but then again the only pc games that interest me are MMO's and lets just say that I've had my fair share playing MMO's and try to avoid them.

---

### Post by veloce on 2008-10-05
Is there some reason that this is easier in OSX? Or is it just easier in the Mac world due to a smaller hardware set?

---

### Post by arang on 2008-10-05
guys, AFAIK the new version of vmware workstation 6.5 got the capability to run direct 3D software in a windows XP virtual machine, i'm gonna test that soon.

---

### Post by go_beep_yourself on 2008-10-06
> **arang said:**
> guys, AFAIK the new version of vmware workstation 6.5 got the capability to run direct 3D software in a windows XP virtual machine, i'm gonna test that soon.

Get back to us on that. I'd really like to know how that works out.

---

### Post by arang on 2008-10-06
i'm right now at work but before i left i was able to install, a few MMORPG Silkroad Online, Lineage 2 and PerfectWorld, and all of them worked flawlessly under vmware workstation 6.5 (and to think that i got the 6.0 with a discount such a great software), they work well, i can notice some hit on the performance but i could say its less than 10% also, i was able to run the games in windowed mode too, (i tested this in a windows XP sp3 VM, with NOTHING installed), i had some weird 3D artifacts with some softening setup, but overall it worked well, i'll see if i can post a few images of my VM.

---

### Post by jcsambo on 2008-10-06
which video display card which fully support ubuntu linux?

thank you.

---

### Post by arang on 2008-10-07
i'm Using a 9600GT with 1Gb RAM with Nvidia drivers from the website, i have added a picture so u all could see it running (if it looks like with lack of detail is cos i have to downsample the image to upload).

BTW for maximum speed i recommend u to play it in full screen and exclusive mode, then it's nearly perfect, downside of it is that u'd need a very powerful machine to do so if u have a 20"+ monitor (1680x1050 or more).

---

### Post by michaelkahl on 2008-10-07
great to hear, I wonder how warhammer does???  I was thinking about picking it up, but then realized that I'd have to install windows, this gives me hope.  I virtualize and I am done.

---

### Post by go_beep_yourself on 2008-10-07
Does the latest Workstation run in a web browser like VM Server does? I hope not. I'll try it out.

---

### Post by arang on 2008-10-07
Vmware workstation works as always, no web browser stuff so dont worry, if only heavy games like bioshock suffer not cos the card or the VM is slow but cos the texture access, i can see in the vmware log that it kept saying that vidmem was exceeded or something, this is cos the virtual video card only allows 256Mb of ram. anyone knows how to put more video memory into the virtual video card?

i get this in the LOG:

Oct 06 23:18:22.584: vcpu-0| Guest: vmx_fb: Ran out of vidmem streaming sysmem execute buffer. <----------- meaning it's using system memory (slow) when it needs more, when it could use more video memory (fast)

---

