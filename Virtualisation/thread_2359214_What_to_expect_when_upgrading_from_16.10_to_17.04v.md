---
title: "What to expect when upgrading from 16.10 to 17.04/virtualbox"
date: 2017-04-21
forum: Virtualisation
---

### Post by smd3 on 2017-04-21
I rely on Virtualbox to run Windows 10 and Office for my class and and work.  I'd like to upgrade from 16.10 to 17.04, but I'm concerned about running into issues with Virtualbox.

Is there anything I can expect, or any resources that discuss this topic?

---

### Post by DuckHook on 2017-04-21
Since you have stated that you are running a production machine that is critical to both school and work, may I ask why you are using a non-LTS version like Yaketty or Zesty? Doing so forces you onto the upgrade treadmill, since non-LTS versions last only 9 months. OTOH, an LTS version like Xenial will remain supported until 2021. If you are concerned about the stability of VBox with version upgrades, then I would suggest that:

[LIST]
[*]This is a legitimate concern. Apps are known to break with upgrades, and
[*]Stability in many areas—not just VMs—is best achieved by sticking with Xenial (16.04)
[/LIST]
In your case, I would further recommend that you stick with the version of VBox in the repos and not use the Oracle PPA that continually upgrades VBox every month.

---

### Post by lammert-nijhof on 2017-04-21
I agree partly with DuckHood, so I run Virtualbox 5.1.18 on 16.04 LTS. I will not upgrade to Vbox 5.1.20, because it does not bring anything of interest for me. Often I skip a number of Virtualbox versions. 

I changed everything this month, I now run my main distros in Virtualbox only. My Host OS is a stripped down version of 16.04, I only use it to manage Vbox (and sometimes to look YouTube video).  So my main distro is another fine tuned Ubuntu 16.04 Guest of Vbox, which I use for all official stuff, like banking, ebay etc. Sometimes when I feel like it, like now I use 17.04, which I use while a Windows XP Guest is playing my music. If you run your main distro as a Vbox guest, you don't have these type of problems, you  clone your 16.10 and upgrade to 17.04. If something goes wrong you still have your 16.10 installation. 

You don't need much, I do it using an old HP PC with a Vista sticker and an old graphics card out of the same Vista period.

Something in 17.04 has a memory leak, because the SWAP file size keeps growing over time, till it reaches its max value after 1 day or so. Maybe a reason to wait till the holiday period with your upgrade.

---

### Post by LastDino on 2017-04-22
Please take snapshot and/or clone your VM installations along with cloning your 16.10 install for backup. 

Technically you should be able to use clone of VM install to run on different mother OS with VM. Here usually catch is hardware and VM settings, but since you're using same machine you should not face huge problems assuming you'll have same VM settings as well. 

NOTE: Try doing this before actually going ahead with the upgrade, test your clones thoroughly. 

And if you're successful, if you don't mind me suggesting, after weekend updates, try to do a clean install instead of upgrade with LTE version as it is you're production machine.

---

### Post by Bucky Ball on 2017-04-22
> **DuckHook said:**
> Since you have stated that you are running a production machine that is critical to both school and work, may I ask why you are using a non-LTS version like Yaketty or Zesty?

+1. You should be running an LTS for this machine if you are using it for what you state. I'm a post-grad student and if I'd had to upgrade my OS every six months for the last ten years I would have lost time I didn't have to lose.

I would have thought that making sure your .vdi file for Win stays intact would be enough and that would launch on any Virtualbox. Maybe I'm wrong.

---

### Post by LastDino on 2017-04-22
> **Bucky Ball said:**
> +1. You should be running an LTS for this machine if you are using it for what you state. I'm a post-grad student and if I'd had to upgrade my OS every six months for the last ten years I would have lost time I didn't have to lose.
[B]
I would have thought that making sure your .vdi file for Win stays intact would be enough and that would launch on any Virtualbox. Maybe I'm wrong[/B].

Yes, generally works. But in one particular instance I had a problem with Guest Windows, I had to reactivate it.  

Later I found out that it had something to do with the settings related to UUID and MAC, though I didn't get around to try it as I've never had to Migrate Windows install to new Ubuntu one as I settled with LTS then.

Better safe than sorry about it and have backups when you can, in my opinion.

---

### Post by Habitual on 2017-04-22
I think Virtualbox Guest additions in 17.04 is causing issues.

I'd export your current Vbox Appliance to file.ova and then secondary storage, just in case.

---

### Post by deadflowr on 2017-04-22
As long as the .vdi file and the .vbox file are intact and not changed, they will run in any virtualbox.
Typically you may need to reset guest additions and expansion packs if changing virtualbox versions.

---

### Post by smd3 on 2017-04-28
This is all good advice, thanks.

I ended up using the live upgrade through the software updater, and everything went fine. Virtualbox works with no issues.

When the next LTS hits, I'll try to stick with it.  It's hard to see new features released, and live without them between LTS releases.

My files are backed up, and /home is on a different physical drive from /.

---

### Post by Bucky Ball on 2017-04-28
Good news. You can mark the thread as 'Solved' to help others from Thread Tools at the top right of this page. Good luck. :)

---

