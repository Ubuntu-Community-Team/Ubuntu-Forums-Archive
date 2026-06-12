---
title: "MD5 Checksum Error"
date: 2005-07-07
forum: Repositories &amp; Backports
---

### Post by SilentGreg on 2005-07-07
Heads up to whomever maintains the repitory:

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb
  MD5Sum mismatch

```

---

### Post by jomk on 2005-07-07
Some more MD5Sum mismatches...

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/aalib1_1.4p5-22_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/aalib1_1.4p5-22_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb)  MD5Sum mismatch

---

### Post by medgno on 2005-07-07
and kwifimanager.

[http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb)

---

### Post by mikebern on 2005-07-07
here are few more that give md5sumn errors

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/libfontconfig1-dev_2.2.3-4ubuntu7_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/libfontconfig1-dev_2.2.3-4ubuntu7_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb)  MD5Sum mismatch

---

### Post by n6mod on 2005-07-07
[QUOTE=mikebern]here are few more that give md5sumn errors

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/libfontconfig1-dev_2.2.3-4ubuntu7_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/libfontconfig1-dev_2.2.3-4ubuntu7_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb)  MD5Sum mismatch[/QUOTE]
 Still more...trying to get php5 built from the dotdeb.org deb-src

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openldap2/libldap2-dev_2.1.30-3ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openldap2/libldap2-dev_2.1.30-3ubuntu3_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/automake/automake1.4_1.4-p6-8_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/automake/automake1.4_1.4-p6-8_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib+png2/gdk-imlib1_1.9.14-16.2ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib+png2/gdk-imlib1_1.9.14-16.2ubuntu2_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11-dev_1.2.0-11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11-dev_1.2.0-11_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.33-1.1ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.33-1.1ubuntu1_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sablotron/libsablot0c102_1.0-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sablotron/libsablot0c102_1.0-1_amd64.deb)  MD5Sum mismatch

---

### Post by SilentGreg on 2005-07-07
Tried running an update on apt, again, still no go. Can't install Firefox 1.0.4.  :neutral: 

Greg

---

### Post by mjbanks on 2005-07-07
I've been trying to install wpasupplicant for the past 2 days and keep getting md5sum errors for anything I try to apt-get... it's getting annoying...

---

### Post by beatyou on 2005-07-08
[QUOTE=mjbanks]I've been trying to install wpasupplicant for the past 2 days and keep getting md5sum errors for anything I try to apt-get... it's getting annoying...[/QUOTE]
 remove .us from your /etc/apt/sources.list

---

### Post by tmunro55 on 2006-11-05
I've just completed a fresh install of Ubuntu 6.06LTS. While trying to retrieve updates using the "Update Manager" I'm getting MD5 Checksum errors. Mostly from  [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu). Is there a problem with the respositories? Could it be a physical connection problem at my end?

Just two weeks ago, I installed the same OS on my laptop and updated it without incident. Using wirelss I go through the same router as my "teathered" machine.

Any help would be greatly appreciated.

---

### Post by tmunro55 on 2006-11-05
specifically here are the problem packages:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.06.2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.06.2_all.deb)
  MD5Sum mismatch

---

### Post by giohappy on 2006-11-28
I have the same problem... Did you solve it?

---

