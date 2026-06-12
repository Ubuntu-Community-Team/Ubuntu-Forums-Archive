---
title: "apt-get problem updating"
date: 2006-08-29
forum: Repositories &amp; Backports
---

### Post by grpprod on 2006-08-29
Hi all,
I just installed my first Kubuntu. I am trying to use apt-get and adept, but I am unable to get any updates. I have commented out the lines in sources.list, and fetched all the updates. But when I actually try to download them adept gives an error.

Running manually, here are (part of) the results. 

[I]Errhttp://au.archive.ubuntu.com dapper-updates/main base-files 3.1.9ubuntu7.1
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main language-pack-en 1:6.06+20060725
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main language-pack-en-base 1:6.06+20060725
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main language-pack-kde-en 1:6.06+20060725
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main language-pack-kde-en-base 1:6.06+20060725
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main wpasupplicant 0.4.8-3ubuntu1.1
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main ubuntu-minimal 0.120
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main ubuntu-standard 0.120
  Connection failed [IP: 195.248.90.54 80]
Errhttp://au.archive.ubuntu.com dapper-updates/main acpi-support 0.85
  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_6.06+20060725_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_6.06+20060725_all.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en-base/language-pack-kde-en-base_6.06+20060725_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en-base/language-pack-kde-en-base_6.06+20060725_all.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_0.120_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_0.120_i386.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-standard_0.120_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-standard_0.120_i386.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.85_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.85_i386.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu6_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu6_i386.deb)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/ept/adept_2.0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/ept/adept_2.0ubuntu2_i386.deb)  Connection failed [IP: 195.248.90.54 80]

[/I]

However, taking one of them for manual download seems to work:

[I]# wget [http://au.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)
--12:34:31--  [http://au.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)
           => `base-files_3.1.9ubuntu7.1_i386.deb'
Resolving au.archive.ubuntu.com... 195.248.90.23, 195.248.90.54
Connecting to au.archive.ubuntu.com|195.248.90.23|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36,652 (36K) [application/x-debian-package]

100%[=======================================================================================================================================>] 36,652        42.64K/s

12:34:32 (42.56 KB/s) - `base-files_3.1.9ubuntu7.1_i386.deb' saved [36652/36652]

[/I]

Any help would be appreciated.

---

