---
title: "apt-get without x packs"
date: 2007-08-16
forum: Server Platforms
---

### Post by mackis5 on 2007-08-16
I would like to install some packs on my ubuntu 7.04 server without getting the X11 packs, since I dont have any X installed.
E.g "apt-get install gnuplot" will install a few X11 dependences, which I dont want.
In gentoo you just add a flag "-X". How is the made in Ubuntu?

---

### Post by Seisen on 2007-08-16
Try installing this package instead, it doesn't have X dependencies.

```
gnuplot-nox
```

---

### Post by kerry_s on 2007-08-16
just in case you didn't know "apititude" is the terminal package manager, it's like the term version of synaptic. alot more detailed than apt-get.

sudo aptitude

---

### Post by mackis5 on 2007-08-16
> **Seisen said:**
> Try installing this package instead, it doesn't have X dependencies.

```
gnuplot-nox
```
Thanks! Seems to work. Is this the case with all different apps? Does a "-nox" always exist?

This is a part of a postinstall of kickstart. I saw that a lot of X11 stuff was installed (i.g openoffice.org wordbook, dont ask me why...) even though I only install the ubuntu-server in my kickstart, without any of the apache, lamp or DNS servers available. Is there a way how I can set the -X flag for the whole kickstart installation?

---

### Post by Seisen on 2007-08-16
Actually gnupt -nolox is a package 

[http://packages.ubuntu.com/feisty/math/gnuplot-nox]("http://packages.ubuntu.com/feisty/math/gnuplot-nox")

---

### Post by Seisen on 2007-08-16
Did you add this option when you created your kickstart file

```
skipx
```

[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-kickstart2-options.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-kickstart2-options.html)

---

### Post by mackis5 on 2007-08-17
> **Seisen said:**
> Did you add this option when you created your kickstart file

```
skipx
```

[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-kickstart2-options.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-kickstart2-options.html)

I am using preseed.cfg and my post install looks like this:
```

d-i pkgsel/include string openssh-server build-essential gnuplot gawk libssl-dev uuid-dev
```

Should I just add "skipx"?```

d-i pkgsel/include string skipx openssh-server build-essential gnuplot gawk libssl-dev uuid-dev
```
or could this be done in a different way?

---

### Post by mackis5 on 2007-08-17
here is my preseed.cfg file. 
```

      d-i mirror/locale string en_US
      d-i console-tools/archs select se_SE
      d-i console-keymaps-at/keymap select se_SE
      d-i netcfg/choose_interface select eht1
      d-i netcfg/dhcp_timeout string 60
      d-i netcfg/get_hostname string unassigned-hostname
      d-i netcfg/get_domain string unassigned-domain
      d-i netcfg/wireless_wep string
      d-i mirror/protocol string http
      d-i mirror/country string enter information manually
      d-i mirror/http/hostname string 192.168.0.1
      d-i mirror/http/directory string /ubuntu
      d-i mirror/http/proxy string

      d-i partman-auto/disk string /dev/sda
      d-i partman-auto/method string regular
      d-i partman-auto/purge_lvm_from_device boolean true
      d-i partman-lvm/confirm boolean true
      d-i partman-auto/expert_recipe string boot-root :: 100 50 100 reiserfs $primary{ } $bootable{ } method{ regular } format{ } use_filesystem{ } filesystem{ reiserfs } mountpoint{ /boot } . 500 10000 1000000000 reiserfs method{ regular } format{ } use_filesystem{ } filesystem{ reiserfs } mountpoint{ / } . 64 512 2048 linux-swap method{ swap } format{ } .
      d-i     partman/choose_partition select Finish partitioning and write changes to disk
      d-i     partman/confirm                 boolean true

      d-i clock-setup/utc boolean true
      d-i time/zone string Europe/Stockholm
      d-i apt-setup/non-free boolean false
      d-i apt-setup/contrib boolean false
      d-i apt-setup/use_mirror boolean false
      d-i apt-setup/security_host string

      d-i debian-installer/allow_unauthenticated string true

      d-i passwd/root-login boolean true
      d-i passwd/root-password password xxxxxx
      d-i passwd/root-password-again password xxxxxxx

      d-i passwd/user-fullname string user1
      d-i passwd/username string user1
      d-i passwd/user-password password xxxxxxx
      d-i passwd/user-password-again password xxxxxxx

      d-i grub-installer/only_debian boolean true

      d-i grub-installer/with_other_os boolean true

      d-i	base-installer/kernel/override-image	string linux-amd64-server
      tasksel tasksel/first string

      d-i     base-installer/kernel/linux/extra-packages-2.6  string
      d-i     archive-copier/desktop-task     string ubuntu-standard
      d-i     archive-copier/ship-task        string
      d-i     pkgsel/install-pattern  string ~t^ubuntu-standard$
      d-i     pkgsel/language-pack-patterns   string

      d-i pkgsel/include string openssh-server build-essential gnuplot gawk libssl-dev uuid-dev

      d-i finish-install/reboot_in_progress note

      d-i preseed/late_command string wget http://192.168.0.1/post_install/server_settings_<COMPUTERNAME>.sh && chmod +x server_settings* && ./server_settings*

```

---

### Post by mackis5 on 2007-08-20
bump

---

### Post by Seisen on 2007-08-20
The skipx option needs to be added to your ks.cfg file in the very first section with all of the other options.

---

### Post by mackis5 on 2007-08-20
> **Seisen said:**
> The skipx option needs to be added to your ks.cfg file in the very first section with all of the other options.
I will try that. 
Thanks

---

### Post by mackis5 on 2007-08-20
> **Seisen said:**
> The skipx option needs to be added to your ks.cfg file in the very first section with all of the other options.

Sorry, one more question.

I am not using a ks.cfg. Instead I am using the preseed.cfg. I find a lot on the net about the ks.cfg but nothing about my method. I tried to use the ks.cfg, but I couldn't get the result I wanted, so I had to use the preseed method.

---

### Post by Seisen on 2007-08-20
Let me look into how to add it to the preseed.cfg and I will get back with you.

---

### Post by Seisen on 2007-08-24
I'm stupid it was staring at me the whole time take out gnuplot and add gnuplot-nox and it should work.

---

### Post by mackis5 on 2007-08-24
> **Seisen said:**
> I'm stupid it was staring at me the whole time take out gnuplot and add gnuplot-nox and it should work.
Thanks,
So the consensus is that no global flags exist. Instead you have to try to find out if -nox packages exists.

---

### Post by Seisen on 2007-08-24
Apparantly, that is the consensus.

---

