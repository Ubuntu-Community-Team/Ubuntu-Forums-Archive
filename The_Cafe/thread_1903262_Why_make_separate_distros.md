---
title: "Why make separate distros?"
date: 2012-01-02
forum: The Cafe
---

### Post by guyver_dio on 2012-01-02
Was thinking, if ubuntu based distros are....based on ubuntu, why offer them as seperate OS's. Could they not be offered as a set of scripts in a package that will configure ubuntu to achieve the same thing? Instead of having to reinstall a seperate OS each time you want to try something different, why not just have ubuntu installed and install a package?

Then maybe there could be some type of snapshot facility that saves your current configuration which can be used to revert back to normal ubuntu. 

They could even be integrated into the installation process of ubuntu without effecting the size. Since you connect to the net during installation process anyway, it could download the scripts+DE+whatever else and reconfigure the installation on the fly.

---

### Post by lukeiamyourfather on 2012-01-02
This isn't an Ubuntu centric discussion. There are many Linux distributions with many different bases. Various Linux distributions exist because the goals and visions differ, sometimes involving upstream things which are not simply handled by installing a new package. While it would make it easier to try different Linux "distributions" it would inherently limit what a Linux distribution could be, which is a step backwards in my opinion.

---

### Post by BrokenKingpin on 2012-01-02
> **guyver_dio said:**
> Was thinking, if ubuntu based distros are....based on ubuntu, why offer them as seperate OS's. Could they not be offered as a set of scripts in a package that will configure ubuntu to achieve the same thing? Instead of having to reinstall a seperate OS each time you want to try something different, why not just have ubuntu installed and install a package?

I agree for a lot of the Ubuntu spin-offs, as a lot of them only offer a slightly different package selections. I think the main reason is that having a already configured distro/ISO is easier when doing a fresh install. Also, having a package that uses a different DE gets a bit messy, as it has to install the new one and remove the old one... feels bit dirty when you are removing and installing that many packages.

---

### Post by keithpeter on 2012-01-02
Hello All

In addition to the other posts...

Some distributions based on Debian or Ubuntu have specialised selections of packages, and the main work is ensuring those packages all work together and have 'sensible' default configurations.

My favourite example is puredyne.org

[http://www.furtherfield.org/interviews/puredyne-discussion-netbehaviour](http://www.furtherfield.org/interviews/puredyne-discussion-netbehaviour)

And also sagemaths

[http://www.sagemath.org/](http://www.sagemath.org/)

Canonical publishes Ubuntu, and needs to make a profit at some point. Issues around branding and interface consistency come into play for them I think. 

If Canonical can find a successful business model, it will be *really* good for the rest of the distros that feed off the base.

---

### Post by grahammechanical on 2012-01-02
I try to keep a few things in mind:

1) Linux distributions are basically a gift from the developers. Certainly no one is charging me for using Ubuntu.

2) Some developers are employed by Commercial organizations. They are paid to code what their employer tells them to code.

3) Many developers give their time and skills freely. They are entitled to work in any direction that gives them satisfaction.

4) If I do not like what is available I am free to get involved in open source development and make things the way I want them to be.

I think that number 4 is the reason that we have so many distributions. It might just be the reason we have Linux distributions at all.

Why is Microsoft Windows described as bloated? Because they tried to make the OS backwards compatible with programs that ran on older versions. No one describes the Apple OS as bloated. Why? Because Apple hardware could not be upgraded and Apple cast adrift older hardware and programs.

If these suggestions were implemented would we end up with bloatLinux or BloatUbuntu?

Regards.

---

### Post by Paqman on 2012-01-02
> **guyver_dio said:**
> why not just have ubuntu installed and install a package?


You can, for the official variants of Ubuntu. Switching from Ubuntu to Kubuntu or vice versa is just a mattter of installing the right packages. The ability you can do this with other Ubuntu-based systems will depend on how extensive the differences are.

---

### Post by aysiu on 2012-01-02
> **guyver_dio said:**
> Was thinking, if ubuntu based distros are....based on ubuntu, why offer them as seperate OS's. Could they not be offered as a set of scripts in a package that will configure ubuntu to achieve the same thing? Instead of having to reinstall a seperate OS each time you want to try something different, why not just have ubuntu installed and install a package? Well, if the people who maintained the remastered Ubuntu variants *wanted* to make a script, they would. As it stands, you can use a metapackage if you want to try out something different (install *kubuntu-desktop*, for example, or use *tasksel* to set up a LAMP server), so the two aren't mutually exclusive. You can download the .iso of the variant if you want, or you can just install the relevant packages.

> Then maybe there could be some type of snapshot facility that saves your current configuration which can be used to revert back to normal ubuntu. Well, if there's a script, then you just do the reverse of the script. What I like to do, when I install a bunch of packages is, before confirming, see what new packages will be installed, highlight them in the terminal and copy and paste them to a text file. That way, if I want to undo it, I can just *sudo apt-get remove* and then paste back what's in the text file.

You can also create a backup image of your Ubuntu installation using various methods (rsync, CloneZilla, Remastersys). 

> They could even be integrated into the installation process of ubuntu without effecting the size. Since you connect to the net during installation process anyway, it could download the scripts+DE+whatever else and reconfigure the installation on the fly. Well, you're assuming you *can* connect to the net during installation, and you can't always do that. Sometimes you have hardware that requires a proprietary driver to be installed to get things working.

In any case, downloading a bunch of packages during installation can take a long time. Why not give people another option? Sure, you can have everyone download the mini.iso (which is 10 MB) and do a net install of everything they want, but people don't always know what they want or don't want (especially if they're new users), and it actually takes longer to do a custom install from mini.iso than to download an entire .iso over BitTorrent of a live/installer CD and install that variant straightaway... also, fewer questions to answer during installation.

Let's take a real-life scenario.

My parents have my old Eee PC 701, and they complained that Windows XP was too sluggish on it, and they wanted me to install Linux on it. By your reasoning, I should have downloaded the Ubuntu .iso, installed Ubuntu (which leaves *very* little space left on a 4 GB SSD), and then manually go through Synaptic to remove all the useless packages and then install a bunch of lightweight substitutes. What a waste of time! Or I could download the mini.iso and then find out that I can't connect my Atheros wireless card through the ncurses installer. Great!

What did I do instead? I downloaded the Lubuntu .iso and installed it, and everything was up and running in 20 minutes. Good thing there's a Lubuntu for my parents.

If you don't like variants, don't use them. Just stick with vanilla Ubuntu. I like having variants, and I even created a variant in the past that others found useful (it had good default settings for the HP Mini 1000 line of netbooks).

---

### Post by alexan on 2012-01-02
> **guyver_dio said:**
> Was thinking, if ubuntu based distros are....based on ubuntu, why offer them as seperate OS's. Could they not be offered as a set of scripts in a package that will configure ubuntu to achieve the same thing? Instead of having to reinstall a seperate OS each time you want to try something different, why not just have ubuntu installed and install a package?

Then maybe there could be some type of snapshot facility that saves your current configuration which can be used to revert back to normal ubuntu. 

They could even be integrated into the installation process of ubuntu without effecting the size. Since you connect to the net during installation process anyway, it could download the scripts+DE+whatever else and reconfigure the installation on the fly.
it does already exist :
Ubuntu server + sudo apt-get install ....

---

