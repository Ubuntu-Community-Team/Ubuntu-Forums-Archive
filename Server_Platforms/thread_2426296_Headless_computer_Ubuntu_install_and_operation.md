---
title: "Headless computer Ubuntu install and operation"
date: 2019-09-06
forum: Server Platforms
---

### Post by dhavalbbhatt2 on 2019-09-06
Hello all,
I am looking to buy a refurbished server, however, I am finding that servers are notoriously bad when it comes to installing simple graphics card that has one or multiple HDMI outputs. So, in order to effectively use it, I am guessing that I will "remote" in to the server (most of the times, I will be on the same network). I think I can manage to remote in using one of the many softwares that are available (I personally like Nomachine, but I digress). 

In any case, the question that I have is, assuming I don't put a monitor in (I really need a monitor with at least 1080p resolution), so the question is, how do I remote in to a machine that does not have a monitor? I do want to be able to "see" the programs running on the server, however, I am guessing that those programs will be seen on the computer from where I remote in - is that correct? Are there any special softwares that I need to install in order to make the visualization possible? Also, should I install the Server edition or should I install the desktop edition (I realize the difference is really in what packages either get installed natively or not at the time of installing a particular edition of Ubuntu) - I am really used to the Desktop edition and the programs (image editing) that I want to run greatly benefit from having a GUI. Is there any documentation that I should be reading to familiarize myself in installing and running a headless computer? 

I am a novice, so please pardon me if I haven't provided all the information and do please feel free to ask me for any other relevant information as it pertains to what I am asking. 

I am hoping folks in here can help.

TIA.

DB

---

### Post by CatKiller on 2019-09-06
Servers are generally headless, which is why they don't come with an array of video outputs; maybe a VGA for emergencies. The server install image is also generally set up to run headless, so it doesn't have a graphical environment at all.

Essentially, if you want graphics then you don't want a server. The term you're looking for, for an overspecced machine that you'll be sat at while you work, is *workstation*.

As a novice who wants to do image editing you just need a bog-standard desktop machine running normal desktop software.

---

### Post by wildmanne39 on 2019-09-06
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by dhavalbbhatt2 on 2019-09-06
> **CatKiller said:**
> Servers are generally headless, which is why they don't come with an array of video outputs; maybe a VGA for emergencies. The server install image is also generally set up to run headless, so it doesn't have a graphical environment at all.

Essentially, if you want graphics then you don't want a server. The term you're looking for, for an overspecced machine that you'll be sat at while you work, is *workstation*.

As a novice who wants to do image editing you just need a bog-standard desktop machine running normal desktop software.

Hi,
Thanks for the advice. I realize that in essence I need a workstation, however, it is a cost thing. A refurbished server is about a 3rd of the price for a similar workstation. 

So, this is as much about cost savings  as it is about being able to access the server remotely. Before I go spend that type of money on a workstation, I was hoping I could ask and find out if what I asked in the original post will actually work or not. 

Thanks and regards! 

DB

---

### Post by TheFu on 2019-09-06
You can build a pretty amazing workstation with 13,000 passmarks for about $300 if you have some common computer parts lying around. Basically, you'd buy a MB, CPU, and RAM, then reuse a GPU, PSU, keybaord, mouse,  case and HDD/SSD you already have.

As for using a server, it will be noisy, generate lots of heat, use way, way, too much electricity, and you'll hate being in the same room with it.  I retired a 2009 Core i7 workstation and my monthly electric bill was at least $10 less.  Have a friend with a dual Xeon server. He can't run it all the time due to the electric costs.  Cheap servers aren't as cheap as they seem in reality.

Servers often don't come with any GPU at all. They are connected via a serial connection to a terminal switch at the head of every row.  These are pure text interfaces - called "console access".  This is what you want when everything isn't working.  A server install wouldn't include **any** GUI programs.

As for remote access, that is what ssh is all about.  Ssh is THE WAY that Unix people connect to systems and do almost everything between systems, using an ssh-based tool.  ssh, scp, sftp, rsync, rdiff-backup, sshfs, and about 50 others included.  ssh makes connections both more secure AND more convenient, plus you won't be bothered to enter a password all the time if you configure it to use ssh-keys with the ssh-agent providing access to the keys as needed.

Nomachine isn't F/LOSS last time I checked.  x2go is. Both use the NX protocol.  Just depends on how much of a purist you are, I suppose.  No remote desktop will work well with video editing. Mine video editor refused to  run without a real GPU, which means I have to sit at the workstation with the GPU.  Remote desktops don't make use of the GPU at this point. Perhaps in a few years they will, but not today, IME.

Forget using a GUI on a server.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is what you need to learn, but ignore any GUI programs.

---

