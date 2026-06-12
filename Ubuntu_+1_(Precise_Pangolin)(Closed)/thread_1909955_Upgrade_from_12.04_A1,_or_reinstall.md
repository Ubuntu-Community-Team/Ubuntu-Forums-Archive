---
title: "Upgrade from 12.04 A1, or reinstall?"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Double.J on 2012-01-16
Hi all, 

I've got 12.04 A1 winging it's way across transmission as I type (I decided I wanted to give it a go before A2 comes out). I'm not a total noob at using linux, having been using deb and SUSE for a couple of years, but I usually only jump in at the beta/RC stage as I start to get a bit impatient about what's coming!

Anyway I've got quite into Ubuntu since 11.10 release (replaced deb as my primary) and want to follow this next release through to final. Usually I try out the pre-release then do a clean install of  the final a week to 10 days after release.

Just wondering what you guys think is best practice; update alpha 1 to 2 to Beta 1 to 2 then reinstall for final, or do a clean reinstall at each stage? 

I suspect I know the answer - reinstall, but just wanted to check :)

Thanks!

---

### Post by effenberg0x0 on 2012-01-16
> **gnu/mirow said:**
> Hi all, 

I've got 12.04 A1 winging it's way across transmission as I type (I decided I wanted to give it a go before A2 comes out). I'm not a total noob at using linux, having been using deb and SUSE for a couple of years, but I usually only jump in at the beta/RC stage as I start to get a bit impatient about what's coming!

Anyway I've got quite into Ubuntu since 11.10 release (replaced deb as my primary) and want to follow this next release through to final. Usually I try out the pre-release then do a clean install of  the final a week to 10 days after release.

Just wondering what you guys think is best practice; update alpha 1 to 2 to Beta 1 to 2 then reinstall for final, or do a clean reinstall at each stage? 

I suspect I know the answer - reinstall, but just wanted to check :)

Thanks!

I don't know how the others work here but I simply update/upgrade my main PC everyday a couple times (maybe 2 or 3 times). I think things never got so borked that I had a true need to reinstall. I would say that unless you're testing the install procedure itself, or the ISOs, I think you can just go on updating daily or every couple days. In my case, my level of customisation is just to high for me to have the energy to endure too frequent full reinstalls. But I never really stopped to think of pros and cons in this method. I see no real relevance, but others will probably have more complete considerations.

When a milestone version is released, like A1, A2, B1, etc I usually just download the ISO and install to a VM for testing purposes: Generally when a user claims to be using a specific alpha/beta release, or when there's some need to diff releases, I clone the related VMs, do what I have to do and delete the clones.

---

### Post by kyleabaker on 2012-01-16
> **gnu/mirow said:**
> Hi all, 

I've got 12.04 A1 winging it's way across transmission as I type (I decided I wanted to give it a go before A2 comes out). I'm not a total noob at using linux, having been using deb and SUSE for a couple of years, but I usually only jump in at the beta/RC stage as I start to get a bit impatient about what's coming!

Anyway I've got quite into Ubuntu since 11.10 release (replaced deb as my primary) and want to follow this next release through to final. Usually I try out the pre-release then do a clean install of  the final a week to 10 days after release.

Just wondering what you guys think is best practice; update alpha 1 to 2 to Beta 1 to 2 then reinstall for final, or do a clean reinstall at each stage? 

I suspect I know the answer - reinstall, but just wanted to check :)

Thanks!

If you're testing to provide feedback or report bugs, I would suggest that you simply update/upgrade so you can help report any introduced issues. I usually update/upgrade all the way to final, then install a fresh final install (this is not necessary, I just like fresh installs).

---

### Post by dino99 on 2012-01-16
you have the best practice yet, and as Precise is a LTS you can jump on board: no huge changes coming, only fine tunes and bug fixes.

---

### Post by Double.J on 2012-01-16
Thanks for the answers guys - glad I asked now! just got done installing; the reason I asked was just to work out what size on disk to assign - if I were to be re-installing every 3-4 weeks, I'd not need as much room as if I' going to run it for 3 months installing all the updates and fixes plus the usual :)

kyleabaker you're quite right I want to start doing my bit ;) though I'd imagine for now it'll just be me finding open bugs and adding my plus one!

---

### Post by ranch hand on 2012-01-16
There is not going to be any difference in size if you just update/upgrade or reinstall.

For instance, you installed A1, that is nice but you also have an awful lot of upgrading to do to catch up with where the OS is today.  If you had used a daily build (assuming it is working today) you would have had, at most, 6 to 12 upgrades.

When upgrades are installed, some things are removed and new things put into packages.  The only thing that builds up to any real extent is your /var/cache/apt/archives where all the packages installed get stored.  Change the preferences so that does not happen or clear it out occasionally.

---

### Post by Double.J on 2012-01-16
Thanks ranch hand, :)

---

### Post by jbicha on 2012-01-16
Also, you'd have old libraries and old kernels around that you should clean. Well, it's probably not worth trying to remove old libraries but a dozen kernels takes up quite a bit of space.

---

### Post by Double.J on 2012-01-16
I like to keep 3 kernel versions, just encase something goes wrong and I didn't notice it was also not functioning in the last one (hard learned lesson). I stick to three, otherwise I find Grub starts to get a bit silly!

---

### Post by paul_in_london on 2012-01-16
In general I just tend to upgrade through each release cycle. I reinstall sometimes (using a daily minimal iso) and then just add what I want on top of that. It's a long time since things have gone so badly wrong that I've **had** to reinstall, but that's partly because with experience you have more idea how to try and fix things. I think at least one of my current precise installs was originally a natty install.

My broken PC has a couple of maverick installs on it so when I finally get it repaired it'll be interesting upgrading those to precise.

---

### Post by cariboo on 2012-01-16
My current install is an upgrade from Natty, it hasn't broken badly enough for me to even think about reinstalling, there a few annoyances, that I haven't got around to fixing yet, but otherwise, things have been pretty stable from the start.

My netbook on the other hand has had several re-installs, but still won't run Precise, it kernel panics after a couple of minutes of logging into the desktop.

---

### Post by kevpan815 on 2012-01-16
> **ranch hand said:**
> There is not going to be any difference in size if you just update/upgrade or reinstall.

For instance, you installed A1, that is nice but you also have an awful lot of upgrading to do to catch up with where the OS is today.  If you had used a daily build (assuming it is working today) you would have had, at most, 6 to 12 upgrades.

When upgrades are installed, some things are removed and new things put into packages.  The only thing that builds up to any real extent is your /var/cache/apt/archives where all the packages installed get stored.  Change the preferences so that does not happen or clear it out occasionally.

Nightly Builds can be risky, and most of the time they do not work for me whenever the CD Image is Over Sized like it is right now even when burning it to DVD, it still does not work on my two Dell Computers.

As a result I usually test only the Mile Stone Builds and Do Not Install any Updates to them as the Updater usually does Not work either. And when it does work, it usually tries to offer me a Partial Upgrade! Just for your information!

---

### Post by kevpan815 on 2012-01-17
> **gnu/mirow said:**
> Hi all, 

I've got 12.04 A1 winging it's way across transmission as I type (I decided I wanted to give it a go before A2 comes out). I'm not a total noob at using linux, having been using deb and SUSE for a couple of years, but I usually only jump in at the beta/RC stage as I start to get a bit impatient about what's coming!

Anyway I've got quite into Ubuntu since 11.10 release (replaced deb as my primary) and want to follow this next release through to final. Usually I try out the pre-release then do a clean install of  the final a week to 10 days after release.

Just wondering what you guys think is best practice; update alpha 1 to 2 to Beta 1 to 2 then reinstall for final, or do a clean reinstall at each stage? 

I suspect I know the answer - reinstall, but just wanted to check :)

Thanks!

You may be unable to Upgrade from Alpha 1, whenever I try it, it always offers me a Partial Upgrade, just for your information!

---

### Post by kevpan815 on 2012-01-17
> **cariboo907 said:**
> My current install is an upgrade from Natty, it hasn't broken badly enough for me to even think about reinstalling, there a few annoyances, that I haven't got around to fixing yet, but otherwise, things have been pretty stable from the start.

My netbook on the other hand has had several re-installs, but still won't run Precise, it kernel panics after a couple of minutes of logging into the desktop.

My Netbook (a 2010 Dell Inspiron 1012 Mini Netbook) will run X64 Ubuntu but not X86 Ubuntu due to a BIOS Compatibility Issue that I read about on either the Ubuntu Wiki or on Launch Pad.

---

### Post by ranch hand on 2012-01-17
Interesting how old some of these installs are.  My oldest started at the end of 9.10-testing (RC I think) and ran great up until the end of 11.10-testing.  It has since had a root transplant and is now Debian Sid.

If you are going to upgrade that A1 puppy, for the sake of your sanity use apt-get, aptitude or synaptic if you must have a gui.

Update Mangler is definitely not the tool for that job.  As you may guess I never use it at all but many folks do.  This job is to upgrade better than a months worth of upgraded packages in a dev release.  Don't even think about using it.

---

### Post by Double.J on 2012-01-17
Thanks for the replies guys, I did put it on a netbook.. how did you all know?! Mine's an NC10 from fall 2008, so it's an N270 with gma945 i.e. BASIC. That said it's taken every 32bit OS I've thrown at it without giving up - including W7 ultimate... and other closed source operating systems ;)

I don't know if it's because I upped the RAM, but it's not having any trouble with running Precise.. fiddled with Compiz a bit and it's running the wobbly windows, workspaces, transparency etc just fine.. Oh and the most important change - using gimp to change the lightdm logo to say 12.04 ;)

To be honest I didn't even know you could update the distro in the GUI.. makes sense I guess! I'm still getting used to some of the GUI tools such as the software centre - I find it's useful for finding packages you don't know, but a cache search does a lot of this, and usually I can update, search and install from the terminal in the time it takes the software centre to load and search ;)

Thanks again all.. Think I'll try upgrading towards release then may consider doing a reinstall of the final, But see how we're looking in April!

Shall mark as solved!

---

