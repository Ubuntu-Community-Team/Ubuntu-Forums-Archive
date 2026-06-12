---
title: "SOAP compiled in PHP"
date: 2007-07-10
forum: Server Platforms
---

### Post by m u r on 2007-07-10
I currently have a server, and I am trying to do something using SOAP. I am getting an error that SOAP is already configured and that I need to do one of the following:
> 1) recompile PHP without soap using a flag (e.g --disable-soap)
2) rename the functions so they are unique
3) disable SOAP in your php.ini (easy & recommended if possible)

Can anyone walk me through the steps to do one of them?

Thanks.

---

### Post by bapoumba on 2007-07-10
@ m u r: I deleted your two other identical threads.
*bumping* this one.

---

### Post by bloon on 2007-08-10
> **m u r said:**
> I currently have a server, and I am trying to do something using SOAP. I am getting an error that SOAP is already configured and that I need to do one of the following:


Can anyone walk me through the steps to do one of them?

Thanks.

Hi,I need to disable Soap client/Server too....anybody knows how to do it on ubuntu php5?

---

### Post by bloon on 2007-08-10
Hi,

I couldn't believe I just solved my own problem...

OK this is what I did to rebuild php5 without soap:



#apt-get remove php5
#apt-get source php5
# apt-get build-dep php5
# cd php*
# cd debian
# nano rules
FRom here...you have to edit on "configure" with "--disable= soap"

Save that edited "rules"


#debuild -us uc

#cd ..

and here we go...you will find brand new php5 with soap disable

# dpkg --install php5*   <<< brand new deb package without soap ready to install

I hope this thing..help anynone who want to build php5 without soap


and you done..

---

### Post by viniciuscarvalho on 2008-01-29
bloon, thanks a lot for the hints. But here, I've done just like you have instructed, but still, it compiled a version with soap enabled :(

Is the code bellow the area we need to change to disable soap?

Regards

```
COMMON_CONFIG=--build=$(PHP5_BUILD_GNU_TYPE)-gnu \
		--host=$(PHP5_HOST_GNU_TYPE)-gnu \
		--mandir=/usr/share/man \
		--enable-memory-limit \
		--disable-debug \
		--with-regex=php \
		--disable-rpath \
		--disable-static \
		--with-pic \
		--with-layout=GNU \
		--with-pear=/usr/share/php \
		--enable-calendar \
		--enable-sysvsem \
		--enable-sysvshm \
		--enable-sysvmsg \
		--enable-track-vars \
		--enable-trans-sid \
		--enable-bcmath \
		--with-bz2 \
		--enable-ctype \
		--with-db4 \
		--without-gdbm \
		--with-iconv \
		--enable-exif \
		--enable-filepro \
		--enable-ftp \
		--with-gettext \
		--enable-mbstring \
		--with-pcre-regex=/usr \
		--enable-shmop \
		--enable-sockets \
		--enable-wddx \
		--with-libxml-dir=/usr \
		--with-zlib \
		--with-kerberos=/usr \
		--with-openssl=/usr \
		--enable-dbx \
		--disable-soap \
		--enable-zip \
		--with-mime-magic=$(MAGIC_MIME) \
		--with-exec-dir=/usr/lib/php5/libexec

```

PS: btw, the debuild does not accepts that last "uc" command. So I've just ran with the -us option

regards

---

