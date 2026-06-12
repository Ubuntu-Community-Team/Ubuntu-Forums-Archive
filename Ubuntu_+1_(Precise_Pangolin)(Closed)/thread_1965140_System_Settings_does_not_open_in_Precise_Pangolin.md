---
title: "System Settings does not open in Precise Pangolin"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ulissipus on 2012-04-25
Just upgraded to Precise Pangolin. Works fine, with some glitches. For instance, some folders - like SYSTEM SETTINGS - will not open. Any clues as to how to correct this?

---

### Post by dino99 on 2012-04-25
System Settings is a feature settings gui, not a folder

---

### Post by ulissipus on 2012-04-25
> **dino99 said:**
> System Settings is a feature settings gui, not a folder

Ok, my mistake, I am a beginner. This feature setting opened in Ocelot and now does not open in Pangolin. What to do?

---

### Post by kansasnoob on 2012-04-25
What method did you use to upgrade?

Have you checked for and applied all updates?

---

### Post by ulissipus on 2012-04-25
> **dino99 said:**
> System Settings is a feature settings gui, not a folder

Perhaps this is not the right place, but I have been having other problems since upgrading to Precise Pangolin. Every now and then an application closes unexpectedly and/or I get a message "system program problem detected". Then I try to report the problem and get the following message:

"The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

gedit, dconf-gsettings-backend, gedit-common, gir1.2-gdkpixbuf-2.0, gir1.2-gtk-3.0, libcups2, libenchant1c2a, libgdk-pixbuf2.0-0, libgssapi-krb5-2, libgtk-3-0, libgtksourceview-3.0-0, libgtksourceview-3.0-common, libjpeg8, libk5crypto3, libkrb5-3, libkrb5support0, libssl1.0.0, perl-base, xz-utils"

Any suggestions on how to proceed? I am a beginner, as I have said, but never had any problems with Ubuntu.

---

### Post by ulissipus on 2012-04-25
> **kansasnoob said:**
> What method did you use to upgrade?

Have you checked for and applied all updates?

I used software upgrade.Somehow upgrade was incomplete and now I am offered partial upgrade, but that does not work. I keep getting messages such as the following one:
[FONT="Book Antiqua"][INDENT]
You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

gedit, dconf-gsettings-backend, gedit-common, gir1.2-gdkpixbuf-2.0, gir1.2-gtk-3.0, libcups2, libenchant1c2a, libgdk-pixbuf2.0-0, libgssapi-krb5-2, libgtk-3-0, libgtksourceview-3.0-0, libgtksourceview-3.0-common, libjpeg8, libk5crypto3, libkrb5-3, libkrb5support0, libssl1.0.0, perl-base, xz-utils[/INDENT][/FONT]

or

[FONT="Book Antiqua"][INDENT]You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs: 

apt, apt-utils, compiz-core, dconf-gsettings-backend, gconf2, gconf2-common, gir1.2-gconf-2.0, gir1.2-gdkpixbuf-2.0, gir1.2-gtk-3.0, gir1.2-vte-2.90, libcompizconfig0, libcups2, libcurl3-gnutls, libgconf2-4, libgdk-pixbuf2.0-0, libgssapi-krb5-2, libgtk-3-0, libjpeg8, libk5crypto3, libkrb5-3, libkrb5support0, libldap-2.4-2, libssl1.0.0, libvte-2.90-9, libvte-common, libxfixes3, openssl, perl-base, python-apt, python-aptdaemon, python-aptdaemon.gtk3widgets, python-dbus, python-gobject, python-pycurl, xz-utils[/INDENT][/FONT]


Any clues on how to proceed? Please bear in mind I am a bit of a beginner. Tks

---

### Post by dino99 on 2012-04-25
sudo apt-get install synaptic
sudo synaptic

then update and look at broken package(s) (if any) on the left pane

---

### Post by grahammechanical on 2012-04-25
If you install a development version of Ubuntu, as you have done, then you should expect issues like the ones you are having. I have been getting messages like that since I started using 12.04 back in November. By doing daily updates those obsolete packages will be replaced and the problem will go away. This is my experience.


You should be able to select System Settings and it should open up a panel with icons for the various settings utilities.

This problem will be resolved when those obsolete packages are replaced. Once, a few months ago, the Software Centre was removed because some of the newer packages were available and were installed but others were not available. A few days later things were resolved and I could re-install Software Centre.

There is a way to fix this, if you do not want to wait.

Install Synaptic Package Manager and use it to search for each of the libraries and mark them for upgrade. They should already be showing a grey coloured icon.

When you are given a list of things that are going to be changed, check the things that are going to be removed and if it is something like Ubuntu-desktop do not allow that to be removed. Go back into Synaptic and remove the check mark against the thing that you do not want to remove.

Regards.

---

### Post by BigSilly on 2012-04-25
I had a similar problem with System Settings, though in my case once I'd selected say, Appearance Settings to change the background, the whole app just hung and its window turned grey. Then once it had sorted itself out, it would take an age to close it. I noticed the CPU going to 100% in System Monitor at the same time. This was just the other day when I had Precise daily installed. I'll try again at release tomorrow.

I dunno if it's related, but it kind of sounds similar to me.

---

### Post by ulissipus on 2012-04-25
Dear Dino999, grahammechanical, BigSilly,
thanks for your advice. I have installed the Synaptic Package Manager but have not had time to run it. Will try and do it tomorrow (in South Africa!)
best regards

---

