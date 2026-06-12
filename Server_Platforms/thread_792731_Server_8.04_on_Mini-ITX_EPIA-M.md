---
title: "Server 8.04 on Mini-ITX EPIA-M"
date: 2008-05-13
forum: Server Platforms
---

### Post by jtbutcher on 2008-05-13
Is it possible to install the server version to a EPIA-M, attempts with both the standard and alternative CD have resulted in the following message:

```

This kernel requires the following features not present on the CPU:
0:6 0:8
Unable to boot - please use a kernel appropriate for your CPU.
```

---

### Post by LoclynGrey on 2008-05-14
Same problem here, i'm looking for fix

---

### Post by windependence on 2008-05-14
If you can't find a workaround, you may want to consider one of the *BSDs like Freebsd. What are you going to do with the box?

-Tim

---

### Post by LoclynGrey on 2008-05-14
I'm not doing anything fancy with my mini-itx board, it's just a spare. My original media server board had some issues (standard pc board), and I thought... I have a mini-itx board somewhere...hmmm
I've had many plans to use it in an exciting project, but never find the time. I've resisted selling it because I know "that" one day I will do a project of some sort,

I figure its better to use it than have it on the shelf.

..still looking for the fix.
I just read on another post that I should try to install a generic kernel, and use that. I'm just working out how to do that. :)

---

### Post by jtbutcher on 2008-05-14
The alternative desktop cd does install ok, moron that i am i had just downloaded another copy of the server cd yesterday ](*,)

Despite the fact that I had not actually been too fussed about having a desktop available, I was a little disappointed to see that it considers 800x600 to be the only viable resolution :(

---

### Post by tweedie on 2009-02-11
probably a little late, but here it goes.  managed to install this on my epia-m cpu with ubuntu 8.04.

1.  Install ubuntu-server as normal
2.  reboot - but with cd server installation still in drive
3.  choose "rescue" and let it go through the motions (ie set up keyboard, etc)
4.  then it will ask you for your root partition.  Select it and then you should get a bash command at the bottom of the screen
5.  you need to install linux-generic - so "apt-get install linux-generic" (might have to sudo it - can't remember!)
6.  thats it.  reboot and you should have now got past the wrong cpu message and get a log in prompt.

Hope that helps!

---

