---
title: "[SOLVED] ebox install requires tons of GUI stuff?"
date: 2008-06-11
forum: Server Platforms
---

### Post by DLLarson on 2008-06-11
I would like to install eBox for Ubuntu Server maintenance. The server manual say the following command will do the job:

sudo apt-get install ebox

Unfortunately this wants to pull in X, gtk, and a whole host of other server unfriendly stuff. Why does eBox require all this stuff?

Is there a way to prevent it?

(BTW... the docs also say you can us virtual package 'ebox-all' to install all of ebox. This doesn't exist.)

---

### Post by Titan8990 on 2008-06-11
Ebox is a GUI program and requires a GUI desktop in order to operate.

---

### Post by DLLarson on 2008-06-12
> **Titan8990 said:**
> Ebox is a GUI program and requires a GUI desktop in order to operate.

This doesn't jibe with the "Ubuntu Server Guide" which lists eBox as the preferred remote server manager. In the manual it says:

> eBox is a web framework used to manager server application configuration. The modular design of eBox allows you to pick and choose which services you want to configure using eBox.

Since Ubuntu Server edition specifically avoids installing X and the rest of the GUI stuff it doesn't make sense provide a tool that requires a GUI. If you look at the eBox project web site it looks like it's only a web app.

I'm sure I could just use Webmin but I'm trying to eval the Ubuntu server as a self-contained product.

Dale

---

### Post by andguent on 2008-06-12
On my Hardy server I tried doing an "apt-get install ebox" and it appears to only be pulling down a very small handful of misc "g" tools, and 50-60 perl libs. Are you definitely getting something different? It does seem very strange that ebox would need anything GUI related. My understanding was that it was all web based configuration.

```
The following packages will be REMOVED:
  libgd2-noxpm
The following NEW packages will be installed:
  ebox gconf2 gconf2-common gettext libapache-authcookie-perl
  libapache-singleton-perl libapache2-mod-perl2 libauthen-sasl-perl
  libcache-cache-perl libchart-perl libclass-container-perl
  libclass-data-inheritable-perl libclass-singleton-perl libclone-perl
  libdatetime-format-mail-perl libdatetime-format-w3cdtf-perl
  libdatetime-locale-perl libdatetime-perl libdatetime-timezone-perl
  libdbd-pg-perl libdevel-stacktrace-perl libdevel-symdump-perl
  libdigest-sha1-perl libebox liberror-perl libexception-class-perl
  libfile-copy-recursive-perl libfile-mmagic-perl libfile-slurp-perl
  libfile-tail-perl libfilesys-df-perl libgconf2-4 libgd-gd2-perl libgd2-xpm
  libglib-perl libgnome2-gconf-perl libgomp1 libhtml-mason-perl libidl0
  libintl-perl libio-socket-ssl-perl libipc-sharelite-perl
  liblog-dispatch-perl liblog-log4perl-perl libmail-rfc822-address-perl
  libnet-ip-perl libnet-jabber-perl libnet-ssleay-perl libnet-xmpp-perl
  liborbit2 libparams-validate-perl libperl6-junction-perl
  libproc-process-perl libproc-processtable-perl libreadonly-perl
  libreadonly-xs-perl libsys-cpu-perl libsys-cpuload-perl libxml-rss-perl
  libxml-stream-perl libxpm4 postgresql postgresql-8.3 postgresql-client-8.3
  postgresql-client-common postgresql-common
0 upgraded, 66 newly installed, 1 to remove and 0 not upgraded.

```

---

### Post by DLLarson on 2008-06-13
> **andguent said:**
> On my Hardy server I tried doing an "apt-get install ebox" and it appears to only be pulling down a very small handful of misc "g" tools, and 50-60 perl libs. Are you definitely getting something different? It does seem very strange that ebox would need anything GUI related. My understanding was that it was all web based configuration.

I think I found the problem. If I do an apt-get dry-run I don't pull in the GUI stuff. If I do a dry-run with aptitude it pulls in the GUI stuff. 

```

The following NEW packages will be automatically installed:
  defoma fontconfig fontconfig-config gconf2 gconf2-common gettext hicolor-icon-theme libapache-authcookie-perl
  libapache-singleton-perl libapache2-mod-perl2 libatk1.0-0 libatk1.0-data libauthen-sasl-perl libbsd-resource-perl
  libcache-cache-perl libcairo2 libchart-perl libclass-container-perl libclass-data-inheritable-perl libclass-singleton-perl
  libclone-perl libdatetime-format-mail-perl libdatetime-format-w3cdtf-perl libdatetime-locale-perl libdatetime-perl
  libdatetime-timezone-perl libdatrie0 libdbd-pg-perl libdevel-stacktrace-perl libdevel-symdump-perl libdigest-sha1-perl
  libdrm2 libebox liberror-perl libexception-class-perl libfile-copy-recursive-perl libfile-mmagic-perl libfile-slurp-perl
  libfile-tail-perl libfilesys-df-perl libfontconfig1 libfontenc1 libfreetype6 libfs6 libft-perl libgconf2-4 libgd-gd2-perl
  libgd2-xpm libgl1-mesa-glx libglib-perl libglib2.0-0 libglib2.0-data libgnome2-gconf-perl libgomp1 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libhtml-mason-perl libice6 libidl0 libintl-perl libio-socket-ssl-perl libipc-shareable-perl
  libipc-sharelite-perl libjpeg62 liblog-dispatch-perl liblog-log4perl-perl libmail-rfc822-address-perl libnet-ip-perl
  libnet-jabber-perl libnet-ssleay-perl libnet-xmpp-perl liborbit2 libpango1.0-0 libpango1.0-common libparams-validate-perl
  libperl5.8 libperl6-junction-perl libpixman-1-0 libpng12-0 libproc-process-perl libproc-processtable-perl libreadonly-perl
  libreadonly-xs-perl libsm6 libsys-cpu-perl libsys-cpuload-perl libthai-data libthai0 libtiff4 libttf2 libx11-6 libx11-data
  libxau6 libxaw7 libxcb-xlib0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxfont1 libxft2
  libxi6 libxinerama1 libxml-rss-perl libxml-stream-perl libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxt6 libxtrap6
  libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 openssl openssl-blacklist postgresql postgresql-8.3
  postgresql-client-8.3 postgresql-client-common postgresql-common ssl-cert ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
  x-ttcidfont-conf x11-common x11-session-utils x11-utils x11-xfs-utils x11-xserver-utils xfonts-encodings xfonts-utils xutils
  xutils-dev
The following packages have been kept back:
  linux-image-server linux-server openssh-server
The following NEW packages will be installed:
  defoma ebox fontconfig fontconfig-config gconf2 gconf2-common gettext hicolor-icon-theme libapache-authcookie-perl
  libapache-singleton-perl libapache2-mod-perl2 libatk1.0-0 libatk1.0-data libauthen-sasl-perl libbsd-resource-perl
  libcache-cache-perl libcairo2 libchart-perl libclass-container-perl libclass-data-inheritable-perl libclass-singleton-perl
  libclone-perl libdatetime-format-mail-perl libdatetime-format-w3cdtf-perl libdatetime-locale-perl libdatetime-perl
  libdatetime-timezone-perl libdatrie0 libdbd-pg-perl libdevel-stacktrace-perl libdevel-symdump-perl libdigest-sha1-perl
  libdrm2 libebox liberror-perl libexception-class-perl libfile-copy-recursive-perl libfile-mmagic-perl libfile-slurp-perl
  libfile-tail-perl libfilesys-df-perl libfontconfig1 libfontenc1 libfreetype6 libfs6 libft-perl libgconf2-4 libgd-gd2-perl
  libgd2-xpm libgl1-mesa-glx libglib-perl libglib2.0-0 libglib2.0-data libgnome2-gconf-perl libgomp1 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libhtml-mason-perl libice6 libidl0 libintl-perl libio-socket-ssl-perl libipc-shareable-perl
  libipc-sharelite-perl libjpeg62 liblog-dispatch-perl liblog-log4perl-perl libmail-rfc822-address-perl libnet-ip-perl
  libnet-jabber-perl libnet-ssleay-perl libnet-xmpp-perl liborbit2 libpango1.0-0 libpango1.0-common libparams-validate-perl
  libperl5.8 libperl6-junction-perl libpixman-1-0 libpng12-0 libproc-process-perl libproc-processtable-perl libreadonly-perl
  libreadonly-xs-perl libsm6 libsys-cpu-perl libsys-cpuload-perl libthai-data libthai0 libtiff4 libttf2 libx11-6 libx11-data
  libxau6 libxaw7 libxcb-xlib0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxfont1 libxft2
  libxi6 libxinerama1 libxml-rss-perl libxml-stream-perl libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxt6 libxtrap6
  libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 openssl openssl-blacklist postgresql postgresql-8.3
  postgresql-client-8.3 postgresql-client-common postgresql-common ssl-cert ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
  x-ttcidfont-conf x11-common x11-session-utils x11-utils x11-xfs-utils x11-xserver-utils xfonts-encodings xfonts-utils xutils
  xutils-dev
0 packages upgraded, 143 newly installed, 0 to remove and 4 not upgraded.

```

This seems like some kind of problem with aptitude or I don't understand some subtle aptitude option I should be using. I guess I'll stick with apt-get.

Thanks for responding!

Dale

---

### Post by dustigroove on 2008-07-09
> **DLLarson said:**
> This seems like some kind of problem with aptitude or I don't understand some subtle aptitude option I should be using. I guess I'll stick with apt-get. Thanks for responding! Dale

Aptitude installs recommended packages by default. To change this behavior, just type “sudo aptitude” without any additional parameters, then Ctrl-T and navigate to the Options menu. It will be one of the settings listed.

Cheers,

---

### Post by jsievert on 2008-08-07
I found something else that caused it on mine.  It requires gd for perl so it install libgd-gd2-perl which requires xpm and that requires x11.  If you first apt-get install libgd-gd2-noxpm-perl and then apt-get install ebox it does not pull in any x11 packages.

---

