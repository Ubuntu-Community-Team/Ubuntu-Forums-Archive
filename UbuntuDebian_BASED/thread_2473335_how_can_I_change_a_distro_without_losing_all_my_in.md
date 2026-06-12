---
title: "how can I change a distro without losing all my information"
date: 2022-04-01
forum: Ubuntu/Debian BASED
---

### Post by dutch249 on 2022-04-01
Hello all,

For a longer time I hardly dare to change the existing distro I am using now (Zorin)
Reason is that I have to re-install the whole system as far as I know.
Besides I have a double boot sometimes.
In short, please help and explain .

Regards,

Hans Minekus / dutch

---

### Post by HermanAB on 2022-04-01
The secret is to install a virtualizer, then you can play without messing up your host.

---

### Post by ActionParsnip on 2022-04-01
By having backups of your important data

---

### Post by coffeecat on 2022-04-01
> **dutch249 said:**
> I am using now (Zorin)

@dutch249, you prefixed your thread "Ubuntu Budgie". That prefix has now gone with the thread move. Zorin is not Ubuntu Budgie, nor is it any of the official flavours of Ubuntu. 

*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Frogs Hair on 2022-04-03
> **dutch249 said:**
> Hello all,

For a longer time I hardly dare to change the existing distro I am using now (Zorin)
Reason is that I have to re-install the whole system as far as I know.
Besides I have a double boot sometimes.
In short, please help and explain .

Regards,

Hans Minekus / dutch

Zorin has no upgrade option yet and a clean installation is required if running an outdated version. 

Zorin 15 is supported until 2023 and 16 until 2025 all older versions are no longer supported.

---

### Post by SeijiSensei on 2022-04-03
A more general answer is to put /home on a separate partition. Then you can update the operating system partition while leaving your files alone.

---

### Post by guiverc on 2022-04-03
I re-install Ubuntu (and *flavor*) systems all the time, without loss of data, and having my *manually installed* package re-installed automatically.

I have a Fedora system that is now a Lubuntu/Kubuntu one, a OpenSuSE system that is now also a Lubuntu/Xubuntu one; none of my data files, configs etc. from either Fedora/OpenSuSE system were lost as I replaced then with Ubuntu/Lubuntu.   (*in fact they've been installed many times by different Ubuntu systems without loss of data.. not always Lubuntu too*)

When a 21.04 system reached EOL somewhat recently, I had no need of it. I didn't need a 21.10 system so *release-upgrade* was no option, so I installed a 22.04 system over it & now it's Ubuntu *jammy*, again no loss of my applications or data files... The 21.04 system was just replaced by 22.04 LTS.

Your question is devoid of any specifics that would allow me to be helpful. Instead I'll note what I consider.

- it's easier if you have a separate /home partition; in fact **mandatory **for some non-Ubuntu OSes.  Ubuntu installs don't need this if using an ISO using either `ubiquity` or `calamares` installer.

- there are problems when you're shifting from one type of package management system to another, ie. with the Fedora & OpenSuSE installations (RPM) I did **not attempt **to have the system auto-reinstall my prior packages; I actually don't believe it's possible, but I wanted to ensure I didn't lose data thus prevented it from being an issue

- not all Ubuntu based systems offer this, and there can be complications with third party packages; but you're devoid of specifics, but it works really well with Ubuntu and [*flavors* of Ubuntu]("https://ubuntu.com/download/flavours"), I know as I have one system I don't perform any upgrades on, and use this type of install to effect my package upgrades *whilst at the same time performing a QA-test install*.

- how easy/difficult it is varies on what system you were using, and **most importantly **and what you didn't specify, what system you're moving to, and what ISO/installer/scripts you install with (*some like Ubuntu provide options*,* some do not*).

---

