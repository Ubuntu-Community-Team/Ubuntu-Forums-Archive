---
title: "Ubuntu CE v3.1 (Feisty) released!"
date: 2007-05-17
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2007-05-17
We have just released an Ubuntu CE v3.1 (Feisty). This is a maintenance release to fix a few bugs. The bug fixes in this release were all reported promptly by Ubuntu CE users and is a testament to the wonderful community that has grown around Ubuntu CE.

The updates are listed below.

- Fixed suspend/hibernate
- Fixed dansguardian proxy issues
- Fixed Ubuntu CE Installer appending wrong sources

Two of these bug fixes are quite significant. It is highly recommended that you use the [convert_me script]("http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/convert_to_ubuntu_christian_edition_feisty.tar.gz") to update your existing Ubuntu CE installation to the latest version.

We have also made some enhancements to the [convert_me script]("http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/convert_to_ubuntu_christian_edition_feisty.tar.gz"). First, there will no longer be a separate script for "conversion" and "upgrading". We have consolidated both scripts into the one [convert_me script]("http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/convert_to_ubuntu_christian_edition_feisty.tar.gz"). Second, we have added some additional error dialogs and messages to help make the conversion/update process go more smoothly.

God Bless, Jereme

---

### Post by kc1di on 2007-05-18
Thank you for your work.

---

### Post by mayfield on 2007-05-18
Sorry but the convert_me_script still does not seem to correct the Ubuntu CE installer problem when installing the Ichthux desktop - error still mentions 'dict-wn'.

---

### Post by tak1150 on 2007-05-18
I read in one of these posts that the new convert_me script would back up the desktop theme, etc files? Is this true? If it is, could you tell us how to get those settings back?

I am using CE 3.0 and not wanting to have to customize desktop things :) Thank you!

---

### Post by mhancoc7 on 2007-05-18
> **mayfield said:**
> Sorry but the convert_me_script still does not seem to correct the Ubuntu CE installer problem when installing the Ichthux desktop - error still mentions 'dict-wn'.

Is the Ubuntu CE Installer still messing up the sources.list file or is it something else? Could you give me some more details on the error that you are receiving?

> **tak1150 said:**
> I read in one of these posts that the new convert_me script would back up the desktop theme, etc files? Is this true? If it is, could you tell us how to get those settings back?

I am using CE 3.0 and not wanting to have to customize desktop things :) Thank you!

The latest convert_me script creates a folder in your home directory named UbuntuCE_Backups. It will contain backups of the personal settings that are modified. It also includes a simple ReadMe file that gives info on what was backed up and where its original location is. You can basically just paste your backups into the correct location. Some of the folders that are backed up have been renamed to make them visible. They simply need to be renamed with a "." in front of the name.

Just let me know if this makes sense.

God Bless, Jereme

---

### Post by mayfield on 2007-05-18
Thanks for your prompt reply.

Ubuntu CE Installer - Install the Ichthux desktop - following error message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ichthux-desktop: Depends: dict-wn but it is not installable
E: Broken packages

Thank you again, Forum response times are simply quite amazing! Free community support is a million times better than paid-for commercial support - spread the word - Linux's true image is an international community of diverse people - fits the Christian ethos perfectly.

---

### Post by mysticrider92 on 2007-05-18
Cool. Now I just have to hunt down the Dansguardian config files so I can download it. The convert_me script merging with the upgrade script is an interesting idea.

---

### Post by mhancoc7 on 2007-05-18
> **mayfield said:**
> Thanks for your prompt reply.

Ubuntu CE Installer - Install the Ichthux desktop - following error message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ichthux-desktop: Depends: dict-wn but it is not installable
E: Broken packages

Thank you again, Forum response times are simply quite amazing! Free community support is a million times better than paid-for commercial support - spread the word - Linux's true image is an international community of diverse people - fits the Christian ethos perfectly.

No problem!

This is actually a problem with the ichthux-desktop meta-package. The Ubuntu CE Installer is basically a front-end for apt-get. The problem is the the dict-wn package is not found in the repos for feisty. Hopefully once Ichthux is updated to feisty this will change.

Sorry for your trouble. 

> **mysticrider92 said:**
> The convert_me script merging with the upgrade script is an interesting idea.

Well, they were basically the same script to begin with. I just had to make a few adjustments. :)

God Bless, Jereme

---

### Post by mayfield on 2007-05-18
Thanks, perhaps Ichthus Installer should be removed until Feisty version is ready - unless this is very soon?

---

### Post by mhancoc7 on 2007-05-18
> **mayfield said:**
> Thanks, perhaps Ichthus Installer should be removed until Feisty version is ready - unless this is very soon?

FYI:
[http://www.ichthux.com/en/node/114](http://www.ichthux.com/en/node/114)

---

### Post by cartuned on 2007-05-20
I too could not install ichthux desktop until I installed the Ubuntu dict-wn package available at 
[http://packages.ubuntulinux.org/hoary/text/dict-wn]("http://packages.ubuntulinux.org/hoary/text/dict-wn") Which produced a "dict-wn_2.og-11_all.deb" package that allowed Ichthux to install with synaptic

Chuck

---

### Post by daller on 2007-06-14
Will ichthux work in Kubuntu 7.04 Feisty Fawn?

---

