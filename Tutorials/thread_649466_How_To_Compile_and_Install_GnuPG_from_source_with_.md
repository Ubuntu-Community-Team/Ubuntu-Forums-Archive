---
title: "How To: Compile and Install GnuPG from source with Camellia and IDEA ciphers"
date: 2007-12-24
forum: Tutorials
---

### Post by kevdog on 2007-12-24
**[SIZE="4"]HowTo Compile GnuPG with IDEA and Camellia Ciphers[/SIZE]**

****[SIZE="4"][COLOR="Red"]Updated to Include GPG and GPG2[/COLOR][/SIZE]**

**[SIZE="3"]PreRequisite Packages for Both Version[/SIZE]**

1. Dependencies: 
   build-essential, linux-header files, subversion, automake

(Cut and paste following inside terminal to install necessary dependencies)
```
sudo aptitude install build-essential linux-headers-$(uname -r) subversion automake checkinstall
```

2. Working Directory Structure (Using this directory structure so guide is coherent.  You may choose to download your svn sources and libs and place them in a different directory)

```

mkdir -p ~/src
cd ~/src
mkdir -p gnupg
mkdir -p gnupg2

```

**[SIZE="5"]Compilation of GnuPG (GnuPG Version 1)[/SIZE]**
***Platforms Tested: Ubuntu, Cygwin (Although installation steps are slightly different)

**[SIZE="3"]Requirements[/SIZE]**
1. SVN sources of GnuPG  
2. IDEA module (Optional)
3. BZIP2 Developmental library

We will be using the GnuPG svn stable branch

**[SIZE="3"]GnuPG (Version 1) SVN Source Files[/SIZE]**

```

cd ~/src
svn co svn://cvs.gnupg.org/gnupg/branches/STABLE-BRANCH-1-4 gnupg
cd gnupg

```

**[SIZE="3"](Optional) IDEA module[/SIZE]**

```

cd ~/src/gnupg/cipher
wget ftp://ftp.gnupg.dk/pub/contrib-dk/idea.c.gz
gunzip idea.c.gz
cd ~/src/gnupg

```

**[SIZE="3"]BZIP2 library[/SIZE]**

```
sudo aptitude install libbz2-dev
```

**[SIZE="3"]Compile GnuPG enabling camellia and idea ciphers[/SIZE]**
```

./autogen.sh --force
./configure --enable-camellia --enable-idea --enable-maintainer-mode
make
make check

Choose one of the Following Options (First Option Recommended if Installing Within the Apt Packaging System):
sudo checkinstall -D --fstrans=no --install=yes --pkgname gnupg --pkgversion svn-`svn info|grep Revision |cut -f2 -d' '`
sudo make install

```

gnupg.exe will be installed to /usr/local/bin.  You need to ensure in your PATH environment variable that /usr/local/bin is listed before /usr/bin (echo $PATH).  This is normally to the case unless the path statement has been modified.

To check the ciphers available with gpg
```
gpg --version
```

Example showing installed gpg version:
```

$  gpg --version
gpg (GnuPG) 1.4.10-svn4881
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH, CAMELLIA128, 
        CAMELLIA192, CAMELLIA256
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```

**[SIZE="3"](Optional)Generating the gpg.conf directory (Needed if going to be modifying default gpg behaivor)[/SIZE]**

```

mkdir -p ~/.gnupg
chmod 600 ~/.gnupg
cp /usr/local/share/gnupg/options.skel ~/.gnupg/gpg.conf

```

I would recommend reading about the various options that can be included/modified in this file, however recommend the following flags be included in the file:

enable-dsa2
personal-cipher-preferences
personal-digest-preferences
personal-compress-preferences
default-preference-list

The preferences above need preferences specified explicitly if wanting to change the default SHA1 digest algorithm to SHA256 or SHA512.
 
------------------------------------------------------------------------------------
**[SIZE="5"]Compilation of GnuPG2 (GnuPG version 2)[/SIZE]**
***Platforms Tested: Ubuntu, (Unable to compile with Cygwin)

**[SIZE="3"]Requirements[/SIZE]**
1. Additional Prerequisite Dependenices needed for GnuPG2
2. SVN sources of GnuPG2

**[SIZE="3"]Additional GnuPG2 PreRequisite Dependencies[/SIZE]**
```

sudo aptitude install libksba-dev libpth-dev texinfo transfig libbz2-dev
cd ~/src
wget ftp://ftp.gnupg.org/gcrypt/libassuan/libassuan-1.0.5.tar.bz2
tar jxvf libassuan-1.0.5.tar.bz2
cd libassuan-1.0.5
./configure && make

Choose one of the Following Options (First Option Recommended if Installing Within the Apt Packaging System):
sudo checkinstall -D --fstrans=no --install=yes --pkgname libassuan --pkgversion 1.0.5
sudo make install

cd ~/src
svn co svn://cvs.gnupg.org/libgcrypt/trunk libgcrypt
cd libgcrypt
./autogen.sh && ./configure --enable-maintainer-mode && make && make check

Choose one of the Following Options (First Option Recommended if Installing Within the Apt Packaging System):
sudo checkinstall -D --fstrans=no --install=yes --pkgname libgcrypt --pkgversion svn-`svn info|grep Revision |cut -f2 -d' '`
sudo make install


```

**[SIZE="3"]GnuPG2 SVN Installation -- Enabling Camellia Cipher[/SIZE]**

```

cd ~/src
svn co svn://cvs.gnupg.org/gnupg/trunk gnupg2
cd ~/src/gnupg2
./autogen.sh --force
./configure --sysconfdir=/etc --enable-maintainer-mode --enable-camellia
make
make check

Choose one of the Following Options (First Option Recommended if Installing Within the Apt Packaging System):
sudo checkinstall -D --fstrans=no --install=yes --pkgname gnupg2 --pkgversion svn-`svn info|grep Revision |cut -f2 -d' '`
sudo make install

```

gnupg2 will be installed to /usr/local/bin.  You need to ensure in your PATH environment variable that /usr/local/bin is listed before /usr/bin.

To check the ciphers available with gpg2
```
gpg2 --version
```

Example showing installed gpg2 version:
```

$   gpg2 --version
gpg (GnuPG) 2.0.10-svn4881
libgcrypt 1.4.1
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, ELG, DSA
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH, CAMELLIA128, 
        CAMELLIA192, CAMELLIA256
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```

**[SIZE="3"](Optional)Generating the gpg.conf directory (Needed if going to be modifying default gpg behaivor)[/SIZE]**

```

mkdir -p ~/.gnupg
chmod 600 ~/.gnupg
cp /usr/local/share/gnupg/options.skel ~/.gnupg/gpg.conf

```

I would recommend reading about the various options that can be included/modified in this file, however recommend the following flags be included in the file:

enable-dsa2
personal-cipher-preferences
personal-digest-preferences
personal-compress-preferences
default-preference-list

The preferences above need preferences specified explicitly if wanting to change the default SHA1 digest algorithm to SHA256 or SHA512.
_________________________________________________
**[SIZE="5"]Updating the GnuPG and GnuPG2 Installation[/SIZE]**

Since both GnuPG and GnuPG2 were installed from svn source packages, it is easy to update the packages when new svn sources are released.


**[SIZE="3"]Updating the GnuPG Installation[/SIZE]**

```

cd ~/src/gnupg
svn up
rm -rf autom4te.cache
./autogen.sh && ./configure --enable-maintainer-mode --enable-camellia --enable-idea && make

Depending on the method Used to Install the Original Installation (Choose One of the following):
sudo checkinstall -D --fstrans=no --install=yes --pkgname gnupg --pkgversion svn-`svn info|grep Revision |cut -f2 -d' '`
sudo make install

```


**[SIZE="3"]Updating the GnuPG2 Installation[/SIZE]**

```

cd ~/src/gnupg2
svn up
rm -rf autom4te.cache
./autogen.sh && ./configure --sysconfdir=/etc --enable-maintainer-mode --enable-camellia && make

Depending on the method Used to Install the Original Installation (Choose One of the following):
sudo checkinstall -D --fstrans=no --install=yes --pkgname gnupg2 --pkgversion svn-`svn info|grep Revision |cut -f2 -d' '`
sudo make install

```

---

### Post by jal on 2008-01-26
Thank you kevdog. I have just made and installed GnuPG with IDEA, couldn't have done it without these instructions.

I do not have msgmerge (Gutsy install), so the autogen.sh script was failing. Commenting out the check allowed it to proceed.

---

### Post by kevdog on 2008-01-26
Could you tell me what msgmerge is??  I'm unfamiliar with this tool and might update the instructions based on your response.

---

### Post by kevdog on 2008-05-25
Updated to include GnuPG and GnuPG2

---

### Post by kevdog on 2008-12-04
Updated to include checkinstall method to introduce installation within the apt packaging system.

---

### Post by jrolland on 2009-01-26
Kevdog,

Thanks so much!! I was beginning to wonder if anyone was ever going to reply to one of my posts!

I had seen this article you reference before, but I was leery about implementing it, because I didn't know how it would interact with apt/synaptic/etc. when new releases came out for GPG on Ubuntu. But I'll give it a shot now that you indicate it is the preferred solution.

By the way (and this is probably better suited for the Absolute Beginner's forum), is there a way to get the source code with apt (or apt-get, etc.) and then build GPG with debuild or something like that (having included the IDEA module, of course)? I think that might be a little better to work with the Ubuntu system.

Thanks again!

Sincerely,
Jeffrey Rolland

---

### Post by kevdog on 2009-01-27
Just my opinion

I would still use the sudo make install method rather than checkinstall to install the svn sources of gnupg.  SVN are the latest and greatest releases, although they might theoretically not be stable (although Ive never run into this situation before!).  The SVN version is usually many generations ahead of the version offered in the Ubuntu repositories and allows for bug fixes.

Because you are compiling from source and installing outside the apt system (when using sudo make install), the binaries will be placed within the /usr/local tree -- such as in /usr/local/bin.  Its possible to keep Ubuntu's repository version installed in the system since this is installed within the /usr tree -- such as /usr/bin.  Hence its possible to have two version of gnupg on the system at the same time.  The directories listed in you $PATH environment variable will show which directory path is preferred, although by default, /usr/local/bin is preferred over /usr/bin.  

There is no other way I know how to get the sources other than from svn or downloading the .tar.gz or .tar.bz2 files directly.  It may be possible to grab the source using apt, however this likely gives you no advantage to using the binary version, since its the same version (although I suppose you could add the idea module into the default source tree).  My recommendation -- stick with svn tree if possible.

Hopefully that answered your questions somewhat!

---

### Post by jrolland on 2009-02-02
OK, I followed the HowTo (so perfectly written - thank you so much!), using the checkinstall option, and gpg now runs fine - with IDEA! - from the command line.

I didn't do the optional "Generating the gpg.conf directory" set of instructions.

However, now I can't use Seahorse. Actually, more precisely, the program "Passwords and Encryption Keys" won't load, and when I double-click on a .gpg (or .pgp) file - or right-click a .gpg (or .pgp) file and select "Open with 'Decrypt File'" - nothing happens.

Is there a simple fix to make this gpg work from the GUI again?

Thanks for all your help!

Sincerely,
Jeffrey Rolland

---

### Post by kevdog on 2009-02-02
I never use seahorse, so I might be out in left field here, but is there a path conflict perhaps -- meaning it can't find it located in /usr/bin?

---

### Post by jrolland on 2009-02-06
When I try to launch seahorse from the command line, I get the error messages

** Message: init gpgme version 1.1.6

** (seahorse:16667): CRITICAL **: init_gpgme: assertion `GPG_IS_OK (err)' failed

** (seahorse:16667): CRITICAL **: seahorse_pgp_source_init: assertion `GPG_IS_OK (gerr)' failed
Segmentation fault

Does this mean anything to anyone?

---

### Post by kevdog on 2009-02-07
Just for the record, I get the same error.  I'm trying to contact the developers on freenode to figure out the mess.  This may take some time however.  The channel is dead.  Hopefully more info later :)

---

### Post by jrolland on 2009-02-19
Actually, it is an easy fix: just open a terminal and type

"sudo ln -s /usr/local/bin/gpg /usr/bin/gpg"

(without the quotes). Works like greased lightning after that.

---

### Post by ayushcena on 2010-01-31
Thanks for the amazing tutorial Kevdog. I was able to install the svn version for gnupg, but when I tried for gnupg2, and typed the command for installing libgcrypt
```
./autogen.sh && ./configure --enable-maintainer-mode && make && make check
```

I get the following error
```
checking for gpg-error-config... no
checking for GPG Error - version >= 1.8... no
configure: error: libgpg-error is needed.
                See ftp://ftp.gnupg.org/gcrypt/libgpg-error/ .

```

This then doesn't let me further install the gnupg2 svn version.

I checked on the website, and the file is a normal text file, so I really don't know what to do with it. I tried just copying it into the folder where I am downloading the libgcrypt, but that doesn't work either. It still gives the same error.

Clearly, even when I trued to run your code for updating the gnupg2 version (hoping it would be updated to a svn version), it gives the same error.

I would be extremely grateful if anyone would help me out with this fix.

Thanks!

---

### Post by kevdog on 2010-02-03
gnupg2 is tricky to get going and sometimes doesn't compile for me at all.  In your case however you are missing the gpg-error library.

In order to do this you need to download the source of libgpg-error:
[http://www.gnupg.org/download/index.en.html](http://www.gnupg.org/download/index.en.html)

And compile it.

Just a summary
download the source
extract it
and then its usually ./config, make, sudo make install

Report back on your success if you have any.
Hopefully that helps.

---

### Post by ayushcena on 2010-02-04
Hey Kevdog,

Thank you for your reply. Unfortunately, it still gives the same error. I downloaded the gzipped file for libgpg-error-1.7, and untarred it, and did the whole deal (./configure, make, sudo make install).

Still, it gives me the same error when I try installing the svn version for gnupg2. The error obtained again is:

```
checking for gpg-error-config... /usr/local/bin/gpg-error-config
checking for GPG Error - version >= 1.8... no
configure: error: libgpg-error is needed.
                See ftp://ftp.gnupg.org/gcrypt/libgpg-error/ .

```

Thanks.

---

### Post by earthmeLon on 2012-07-22
Thanks for this great walk-through.  I'm attempting to install gpg from the latest git.


```
$ ./configure --sysconfdir=/etc --enable-maintainer-mode --enable-camellia
...
configure:
***
*** You need libassuan to build this program.
*** This library is for example available at
***   ftp://ftp.gnupg.org/gcrypt/libassuan/
*** (at least version 2.1.0 (API 2) is required).
***
configure:
***
*** It is now required to build with support for the
*** New Portable Threads Library (nPth). Please install this
*** library first.  The library is for example available at
***   ftp://ftp.gnupg.org/gcrypt/npth/
*** (at least version 0.91 (API 1) is required).
***
configure: error: 
***
*** Required libraries not found. Please consult the above messages
*** and install them before running configure again.
***

```

Unfortunately, I am unable to find source or debs for the required libraries.  Do you have any suggestions?

Although Camellia interests me, my biggest goal is the ability to use 8192 RSA keys.

Thanks again

---

### Post by Tex-Twil on 2013-03-19
Hi,
the idea.c file is not available anymore in 

```

[ftp://ftp.gnupg.dk/pub/contrib-dk/idea.c.gz](ftp://ftp.gnupg.dk/pub/contrib-dk/idea.c.gz)

```

where can I get it ?

---

