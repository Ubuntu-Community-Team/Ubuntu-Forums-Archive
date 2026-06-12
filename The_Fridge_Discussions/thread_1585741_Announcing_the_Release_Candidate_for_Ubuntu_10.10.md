---
title: "Announcing the Release Candidate for Ubuntu 10.10"
date: 2010-09-30
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-09-30
Releases are big. You just won&#8217;t believe how vastly, hugely, mind-bogglingly big they are. I mean, you may think it&#8217;s a long haul to release a single Linux package or application, but that&#8217;s just peanuts to a Linux distribution release. Because of this, we must work our way up to it, incrementally&#8230;bit by bit&#8230;milestone by milestone&#8230;it takes a lot of Deep Thought. So with that, we formally announce Ubuntu 10.10 Release Candidate.  Codenamed "Maverick Meerkat", 10.10 continues Ubuntu&#8217;s proud tradition of integrating the latest and greatest open source technologies into a high-quality, easy-to-use Linux distribution.

We consider this release candidate to be complete, stable, and suitable for testing by any user.

Ubuntu 10.10 Desktop Edition and Ubuntu 10.10 Netbook Edition continue to focus on delivering cutting edge technologies, while preserving a crisp and clean user-focused experience.

Kubuntu 10.10 merges the desktop and netbook images into one download and features a new application focused software manager.

Ubuntu 10.10 Server Edition provides even better integration of the Ubuntu Enterprise Cloud and other key features such as: Hadoop, Web2.0 workloads, and hypervisor technologies.

Ubuntu 10.10 Server for UEC and EC2 brings the power and stability of the Ubuntu Server Edition to cloud computing, whether you&#8217;re using Amazon EC2 or your own Ubuntu Enterprise Cloud.

Release Candidates have also been released for several Ubuntu variants, Xubuntu, Edubuntu, Ubuntu Studio, and Mythbuntu.

[http://www.ubuntu.com/getubuntu/releasenotes/1010](http://www.ubuntu.com/getubuntu/releasenotes/1010) 

In addition, there are a small number of known bugs in the release candidate that will be fixed before the Ubuntu 10.10 release, but warrant highlighting for your attention:

[http://www.ubuntu.com/getubuntu/releasenotes/1010#Known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/1010#Known%20issues) 

Ubuntu Desktop features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

The GNOME base platform has been updated to the current 2.32 versions. This includes the new dconf and gsettings API. 

Evolution was updated to the 2.30.3 version, which operates much faster than the version in Ubuntu 10.04 LTS. 

Shotwell has replaced F-Spot as the default photo manager.

Gwibber has been updated to support the recent change in Twitter&#8217;s authentication system, as well as changing the back end storage to improve performance.

The Sound Indicator has been enhanced to include music player controls.

The Ubuntu Software Center has an updated look and feel, including the new "Featured" and "What&#8217;s New" views for showcasing applications, and an improved package description view. You can now easily access your package installation history, too.

New Design: The boot process is cleaner and faster. New themes, new icons, and new wallpaper bring a dramatically updated look and feel to Ubuntu.

Ubuntu One: Polished desktop integration with new sign up and sign in process. Tighter integration with Ubuntu SSO. Nautilus enhancements for managing folder sync preferences. Faster file sync speed. Share links to music within the Ubuntu One Music Store.

Ubuntu Server features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

Cloud computing:  The configurable initialization process for Ubuntu Server cloud images (cloud-init) has gained new features in Maverick Beta, including pluggable hooks, ebsmount, ext4 support, and new stanzas in the cloud-config format.  Cloud image instances can now manage their own kernel and upgrade kernels with apt. This is done by using pv-grub, provided by Amazon. 

Ubuntu Netbook features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

The new Unity interface is now the default in Ubuntu Netbook Edition. It includes places for launching applications and browsing files, semantic search through the usage of zeitgeist, optimizing vertical space with a global menu bar and maximizing application by default. A launcher is also available for keeping and dealing with mostly used applications. All favorites from UNE lucid or gnome panel items and desktop shortcuts are automatically transitioned to the launcher on first run.

In addition to that, the date and time indicator now has a real calendar widget and is included by default. Evolution is now performing a special mode more suited for netbook screen size.

The standard photo management application has been switched to Shotwell and UNE comes will all goodness of the Desktop Edition too. 

UNE needs graphical driver acceleration to be able to run. Otherwise, you should be warned about missing them and will be logout and proposed to run standard ubuntu desktop session.

Kubuntu features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

For Maverick, Kubuntu have merged the Desktop and Netbook images into one. Either Plasma Desktop or Plasma Netbook workspace will be started at login as best suits your computers. Users will be able to switch between the two in System Settings.

Plasma Netbook now sports the Global Menu by default.

The standard web browser is now Rekonq, a KDE browser based on Qt Webkit.

Bluedevil has become the default bluetooth stack.

Pulseaudio is the default sound server.

KPackageKit updates bring a faster backend and an updated UI that provides an application focused view.

Kubuntu&#8217;s installer, Ubiquity, now starts the install as soon as disks are configured, and offers the option to install restricted packages during the install. Qapt-batch now replaces install-package as the update/batch-installer utility

KDE Platform, Workspaces, and Applications have been updated to 4.5.1

Qt was updated to the new 4.7 release.

Kubuntu Mobile Tech Preview is a new variant with a workspace suitable for smart phones.

See [https://wiki.kubuntu.org/MaverickMeerkat/RC/Kubuntu](https://wiki.kubuntu.org/MaverickMeerkat/RC/Kubuntu) for more details.

Xubuntu features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

Xfce4 was updated to the current 4.6.2 release.

New default applications include: Parole (Xfce4 Media Player), replacing Totem Movie Player; Xfburn (Xfce4 CD/DVD burning tool), replacing Brasero; and xfce4-taskmanager (Xfce4 process manager), replacing Gnome-Task-Manager. 

Edubuntu features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

Edubuntu now includes Gnome Nanny, which provides parental controls in Edubuntu. There is new wallpaper included (periodic table breakout). In addition, an OEM Install mode is now available.

For those interested in learning more, there&#8217;s a new web site as well. Check out [http://www.edubuntu.org](http://www.edubuntu.org). 

Ubuntu Studio features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

In this release, Ubuntu Studio has better integration between Pulse Audio and JACK. JACK and Pulse Audio can now be used side-by-side if they are using different audio interfaces. If they are trying to use the same audio interface, JACK will take precedent. The network connections can now be configured with gnome-network-admin. 

Mythbuntu features
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

In this release, Mythbuntu has updated to MythTV 0.23.1. 

There is also a new backup and restore tool.

Other
&#8212;&#8212;-

[LIST]
[*]On the Desktop: GNOME 2.32, KDE Platform 4.5.1, Xfce 4.6.2, OpenOffice.org 3.2.1, X.org server 7.5
[*]On the Server: Apache 2.2.16, PostgreSQL 8.4.4, PHP 5.3.3, LTSP 5.2.4"Under the hood": Linux 2.6.35.4, GCC 4.4.5 (default) / 4.5.1 (optional), eglibc 2.12.1, Python 2.6.6 (default) / 3.1.2 (optional)
[/LIST]The full release notes can be found at [http://www.ubuntu.com/getubuntu/releasenotes/1010](http://www.ubuntu.com/getubuntu/releasenotes/1010) 

About Ubuntu
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

Ubuntu is a full-featured Linux distribution for desktops, laptops, and servers, with a fast and easy installation and regular releases.  A tightly-integrated selection of excellent applications is included, and an incredible variety of add-on software is just a few clicks away.

Professional technical support is available from Canonical Limited and hundreds of other companies around the world.  For more information about support, visit [http://www.ubuntu.com/support](http://www.ubuntu.com/support) 

To Get Ubuntu 10.10 RC
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

To upgrade to Ubuntu 10.10 RC from Ubuntu 10.04 LTS, follow these instructions:

  [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades) 

Or, download Ubuntu 10.10 RC; The following link will direct you to a download location near you:

  [http://www.ubuntu.com/testing/download](http://www.ubuntu.com/testing/download) (Ubuntu Desktop, Server, and Netbook) 

  [http://uec-images.ubuntu.com/releases/10.10/rc/](http://uec-images.ubuntu.com/releases/10.10/rc/) (Ubuntu Server for UEC and EC2)
  [http://releases.ubuntu.com/kubuntu/10.10/](http://releases.ubuntu.com/kubuntu/10.10/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/10.10/rc/](http://cdimage.ubuntu.com/xubuntu/releases/10.10/rc/) (Xubuntu)
  [http://cdimage.ubuntu.com/edubuntu/releases/10.10/rc/](http://cdimage.ubuntu.com/edubuntu/releases/10.10/rc/) (Edubuntu DVD)

  [http://cdimage.ubuntu.com/ubuntustudio/releases/10.10/rc/](http://cdimage.ubuntu.com/ubuntustudio/releases/10.10/rc/) (Ubuntu Studio)
  [http://cdimage.ubuntu.com/ubuntu-netbook/ports/releases/10.10/rc/](http://cdimage.ubuntu.com/ubuntu-netbook/ports/releases/10.10/rc/) (Ubuntu ARM)
  [http://cdimage.ubuntu.com/mythbuntu/releases/10.10/rc/](http://cdimage.ubuntu.com/mythbuntu/releases/10.10/rc/) (Mythbuntu)

  [http://cdimage.ubuntu.com/kubuntu-mobile/releases/10.10/rc/](http://cdimage.ubuntu.com/kubuntu-mobile/releases/10.10/rc/) (Kubuntu Mobile Preview)
  [http://cdimage.ubuntu.com/kubuntu-mobile/ports/releases/10.10/rc/](http://cdimage.ubuntu.com/kubuntu-mobile/ports/releases/10.10/rc/)  (Kubuntu Mobile Preview ARM) 

Please download using Bittorent if possible. 

The final version of Ubuntu 10.10 is expected to be released in October 2010.

Feedback and Participation
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

If you would like to help shape Ubuntu, take a look at the list of ways you can participate at

  [http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/) 

Your comments, bug reports, patches and suggestions will help turn this Beta into the best release of Ubuntu ever.  Please note that, where possible, we prefer that bugs be reported using the tools provided, rather than by visiting Launchpad directly.  Instructions can be found at

  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) 

If you have a question, or if you think you may have found a bug but are not sure, first try asking on the #ubuntu IRC channel on freenode, on the Ubuntu Users mailing list, or on the Ubuntu forums:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-users](http://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/) 

More Information
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

You can find out more about Ubuntu and about this preview release on our website, IRC channel and wiki. If you are new to Ubuntu, please visit:  

  [http://www.ubuntu.com/](http://www.ubuntu.com/) 

To sign up for future Ubuntu announcements, please subscribe to Ubuntu&#8217;s very low volume announcement list at:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce) 

Originally sent to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000138.html") by Robbie Williamson on Thu Sep 30 18:46:26 BST 2010



[More...](http://fridge.ubuntu.com/node/2136)

---

