---
title: "Ubuntu 9.04 in Microsoft Virtual PC"
date: 2009-09-08
forum: Virtualisation
---

### Post by michellez on 2009-09-08
Before any one says anything - I know - Virtual PC! - I don't have a choice though as much as I would prefer to use VM Ware or Virtual Box etc :(

I managed to get it to go through the install process by following this guys blog post [http://www.myoddweb.com/2009/07/03/install-ubuntu-9-on-virtual-pc-2007/]("http://www.myoddweb.com/2009/07/03/install-ubuntu-9-on-virtual-pc-2007/")

When I boot it afterwards it fails tho. Found a few people describing the problem but no fix. Annoyingly one person replied with a something along the lines of "yeh I got it working in virtual pc but decided to use virtual box in the end" but didn't explain what he had to do to get it to work!

I boot it...
* You get the bios
* Then: GRUB Loading stage1.5
Please Wait, Grub loading etc with it counting down
* Then the "Boot from (hd0,0) ext3 ..." screen
* Then... lots of stuff scrolls by!
[IMG]http://www.elseif.co.uk/~shell/stuff/ubuntuvpc.jpg[/IMG]

The last few lines are the ones that catch my eye?
```

[   2.548005]  [<c07378ed>] start_kernel+0x300/0x37c
[   2.548005]  [<c07373a4>] ? unknown_bootoptio0x0/0x1f8
[   2.548005]  [<c0737099>] __init_begin+0x99/0xa1
[   2.548005] ---[ end trace 4eaa2a86a8e2da22 ]---

```

Any ideas guys? It would **really** be appreciated! :)

Thanks,
Shell

---

### Post by dk06 on 2009-09-09
From what I remember, Microsoft's Virtual PC is designed to run Windows based VMs and doesn't have much support for Linux. I suggest Sun's VirtualBox as an easy, more flexible solution for Microsoft and Linux guest OSes. 

Just my opinion

---

### Post by michellez on 2009-09-09
I do not have local admin rights on the PC I am doing this on. I simply do not have the option of using something other than Virtual PC. I know it's not "designed" for it but I have seen while searching enough saying it worked for them no problems!

Meh! :(

Thanks,
Shell

---

### Post by 3rdalbum on 2009-09-09
You might need to turn off certain things like ACPI in the GRUB menu, or turn off certain features of Virtual PC; it's crashing the kernel only two and a half seconds in.

---

### Post by dk06 on 2009-09-09
You can use wubi on a windows installation???? lol...or you can try the suggestions on these links:

[http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/](http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/)
[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)
[http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx](http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx)
[http://rtipton.wordpress.com/2008/02/17/virtual-pc-and-ubuntu/](http://rtipton.wordpress.com/2008/02/17/virtual-pc-and-ubuntu/)

I'm not sure what's going on with the errors but if you want to start fresh with the above links, it looks like they were able to make it work

---

### Post by dalefrancis88 on 2009-10-07
this happens when you disable 'hardware virtulization' or you cant do it. enable it and it should work :)

---

### Post by peterhof on 2009-10-08
Try having a look at this post, managed to get it working after following some instructions here:

[http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html](http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html)

HTH

---

