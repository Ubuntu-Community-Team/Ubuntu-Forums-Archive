---
title: "Update Fatigue"
date: 2024-10-16
forum: The Cafe
---

### Post by makitso on 2024-10-16
Been a user of *ubuntu since 8.04.  However, I am getting on in years the upgrading from 22.04 LTS to 24.04 was a real pain in the ars – my main driver is currently stuck on 22.04.  


So, my question is, are rolling distributions a viable alternative or am I trading one problem for another?  
I have looked at Solus but am concerned about its long term viability.  Looked at Debian testing and it’s too much for me and my preferred Budgie desktop.


One options is to stay with 24.04 and Ubuntu Pro and never upgrade again.


Is there any safe harbor?

---

### Post by Tadaen_Sylvermane on 2024-10-16
Everything needs upgrades. Even if you pick a rolling  release you are just changing to a lifetime upgrade process, and just because it's rolling doesn't guarantee you won't have issues. A computer's software can only last so long unless you can find people to keep up with security issues and such. At some point though patching a given version of a package becomes far more work than just distributing an upgraded package altogether.

I can only assume main driver is a video driver. I know my wife's computer is rather old, it's just an office computer I tossed an old low profile Nvidia gpu in. The Nvidia driver in 24.04 doesn't work for it, nouveau being the only option. This driver stutters like hell on Minecraft. Proprietary driver is buttery smooth. So it is stuck on 22.04. In this case I changed it to Zorin. With Ubuntu Pro 22.04 will be updated for another 7 or 8 years (given the advertised 10 year support period). That is plenty of time and no rush to update. I'd say stick with Jammy and don't sweat it. A lot can happen in that time frame. You may not even have to worry about it as the computer may die or something, then you'd be forced to upgrade anyway.

I don't know if you installed the Budgie desktop on Ubuntu or use that derivative release Ubuntu Budgie. The best path in your case I see is to use a proper Ubuntu Jammy installation, then just add the Budgie package. You may need to do some configuration to match what the derivative may do. I don't know. But that will give you the ESM support for the bulk of your packages into 2032. This will keep your driver set. If you want to stick with 24.04 then it will be good till 2034. A good long time and perfectly good with the Ubuntu Pro. However you don't have your main driver in that so it won't be ideal. Depends on how important that main driver is to you.

---

### Post by oldfred on 2024-10-16
I updated every release from 6.06 to 9.04? But then converted from 32bit to 64 bit with new install.
New install was so much easier than upgrade (back then) that I only have used new installs.

I separate system from data, and have at least two / (root) partitions current LTS and previous/future LTS and link to data. I may install each 6 month release just to see differences, but in another / partition.

---

### Post by 1fallen on 2024-10-16
> **makitso said:**
> 

So, my question is, are rolling distributions a viable alternative or am I trading one problem for another?  
I have looked at Solus but am concerned about its long term viability.  Looked at Debian testing and it&#8217;s too much for me and my preferred Budgie desktop.

Is there any safe harbor?

No Safe Harbor.....
I myself have found rolling releases to be more stable than Buntu, with well over 10 yrs now. I find Drivers (Video) to be again more stable than Buntu.

However Tadaen_Sylvermane gives a good warning on that subject. 

Now that I have mentioned stability with Arch Rolling, it always comes with a learning curve. And I find most users shoot themself in foot.

But I always say just use what works for you. Times Change and we need to do the same.

KEY NOTE: Back-ups are so very important to or for *any* system.

---

### Post by Dennis N on 2024-10-16
I have an Ubuntu 18.04 LTS enrolled with Pro. It's hassle free. I use Flatpaks in cases when I want a newer version of an application. 
I am probably going to do the same with my current Ubuntu 24.04 LTS at some point.
I have read that Ubuntu 'flavors' can also use Ubuntu Pro.

---

### Post by makitso on 2024-10-16
[COLOR=#000000][FONT=Arial]Thanks for all your good comments[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have three laptops, all with LUKS encrypted home partitions and dual boot, all on Ubuntu Budgie 22.04. One laptop is an old ThinkPad and when I booted the 24.04.1 liveCD it hung before I even got to the install.  The second Laptop is a newer Dell and is pretty stock, it upgraded OK.  The third laptop is my busy (LAMP) daily driver Dell XPS.  I tried an update and the resulting system was very unstable.  I tried a clean install and it borked due to the LUKS partition.  [/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Aside From moving to a Mac &#8211; I actually have one in my closet, there really doesn't appear to be any good option aside from sticking to 22.04 Pro and waiting for it to go toes up.[/FONT][/COLOR]

---

### Post by Shibblet on 2024-10-16
> **makitso said:**
> So, my question is, are rolling distributions a viable alternative or am I trading one problem for another?
My go-to for the longest time was Manjaro, which is a "rolling-release" distro.  It has all the packages that I need, as well as access to the AUR.  However, upgrading/updating was always a major issue for me, because every time there was a "system upgrade" for Manjaro, it would break... I don't know... something... and then not work.  I'd have to download the new ISO and re-install.

It's not that I couldn't have troubleshooted the issue... it was just quicker for me to re-install.

> **makitso said:**
> Is there any safe harbor?
Manjaro is the only rolling release that I have used.  And many people say the same thing about it's major updates.  They tend to break things.  So, I am back to Kubuntu, and doing the LTS releases.

I'm not sure if there is a "safe harbor" for any OS.  Microsoft Windows breaks things on major updates as well.  I hear SuSE is very stable.

---

### Post by Rubi1200 on 2024-10-16
I recently moved to the Arch-based rolling release in the form of EndeavourOS.

In terms of updating/upgrading through two major releases as well as the regular cycle of updates, I have found it to be smooth and hassle-free.

Of course, as we all know...backups are vital.

---

### Post by bernard010 on 2024-10-29
My go to is MX-Linux a semi-rolling release. Stable for the last 10 years.
I QA Test Ubuntu in virtual box. Have had some problems with Ubuntu over the years. 
I still enjoy Ubuntu very much. I like the snap packages idea.
I upgraded Ubuntu 3 times it worked just fine twice, once it left me at grub.
I do agree that a new install works the best of all.

---

