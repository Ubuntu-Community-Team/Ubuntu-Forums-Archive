---
title: "Keep the kids from removing the proxy setup"
date: 2008-02-19
forum: Ubuntu Christian Edition
---

### Post by manfarb on 2008-02-19
Just wanted to post this information because I'm quite excited how easy it was to setup.  I recently installed Ubuntu Christian Edition 7.04 on a dedicated box (P3-500 with 384 MB RAM and 10GB hard drive) and assigned it a static IP.  The very cool thing about CE 7.04 is that it has DansGuardian installed with a GUI to administrate it.  I think it has a couple of other little apps running to make this whole thing happen that I'm describing, but who cares, they're all installed by default and I didn't have to do a thing to configure it.  Gotta love that.

So what I wanted to do is use the CE box as a proxy server to provide parental controls for my 3 boy's PCs, which are running Windows Vista and XP.  All I had to do is simply point their browsers to use the proxy server at the IP address I assigned to the CE box, at port 8080 of course.  They all use IE and Firefox, so I configured both.  I found this information in the Ubuntu forum, and probably a couple of other places too.  The problem of course is that my 3 boys are easily smart enough to go into the their browser's connection settings and remove my work to point them to my CE box.  So here's what I did.

We all sit behind a Linksys WRT54G router.  The router allows me to add their MAC addresses to a list and deny them Internet access.  So now if they remove the proxy settings in their browser connection settings, they don't have Internet access.  The only way they can get access is through the CE box's proxy server.  Is that awesome or what?  So there we go.  I just set this up like about an hour ago, so if I have any additional information to add as the boys start using things, I'll post it.

Oh, and for those of you that are worried about the carbon footprint of running a dedicated box for parental controls, in my case I already run a Ubuntu box as a server for my business, so I've got a new low-power motherboard on order and plan to convert my server running Ubuntu desktop version 7.10 (I find the desktop version is fine for what I need) to a Ubuntu CE desktop version 7.04 and use it for my business stuff and the proxy server for the boys.  It will be a thing of beauty!

---

### Post by theophile on 2008-02-19
Well done!

I know how you feel. I totally geek out about stuff like this too.

I just finished flashing a 3rd party firmware to my WRT54G so I can use the router to ping OpenDNS whenever the ip address changes. In my case, the access restrictions are for *me* and i I had used ddclient, my wife's password would have been in a plaintext config file. This way, she sets the password for OpenDNS and the password for the router and I'm at her mercy. Just the way she likes it.

---

