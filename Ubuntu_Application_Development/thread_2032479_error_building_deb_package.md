---
title: "error building deb package"
date: 2012-07-24
forum: Ubuntu Application Development
---

### Post by duffrecords on 2012-07-24
I'm trying to build a deb of a more recent version of Nginx.  It compiles successfully but then fails during the install stage:```
install -m644 debian/nginx.ufw.profile debian/nginx/etc/ufw/applications.d/nginx
install: cannot create regular file `debian/nginx/etc/ufw/applications.d/nginx': No such file or directory
make: *** [install] Error 1
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc -i failed
```It looks like it's trying to copy files to a directory that doesn't exist.  Do I simply add a "mkdir" command to the rules file?  I got the rules file from running "apt-get source nginx" and modifying the configure options.  What am I missing?```
#!/usr/bin/make -f

CFLAGS = -Wall -g

DEB_BUILD_ARCH ?=$(shell dpkg-architecture -qDEB_BUILD_ARCH)
ifneq (,$(findstring sparc,$(DEB_BUILD_ARCH)))
   CONFIGURE_OPTS = --with-cc-opt="-m32 -mcpu=ultrasparc"
endif

ifneq (,$(findstring noopt,$(DEB_BUILD_OPTIONS)))
	CFLAGS += -O0
else
	CFLAGS += -O2
endif

config.status:
	dh_testdir
ifneq "$(wildcard /usr/share/misc/config.sub)" ""
		cp -f /usr/share/misc/config.sub config.sub
endif
ifneq "$(wildcard /usr/share/misc/config.guess)" ""
		cp -f /usr/share/misc/config.guess config.guess
endif
	./configure --conf-path=/etc/nginx/nginx.conf \
	    --error-log-path=/var/log/nginx/error.log \
	    --pid-path=/var/run/nginx.pid \
	    --lock-path=/var/lock/nginx.lock \
	    --http-log-path=/var/log/nginx/access.log \
	    --http-client-body-temp-path=/var/lib/nginx/body \
	    --http-proxy-temp-path=/var/lib/nginx/proxy \
	    --http-fastcgi-temp-path=/var/lib/nginx/fastcgi \
	    --with-debug \
	    --with-http_stub_status_module \
	    --with-http_flv_module \
	    --with-http_ssl_module \
	    --with-http_dav_module \
	    --with-http_gzip_static_module \
	    --with-http_realip_module \
	    --with-mail \
	    --with-mail_ssl_module \
	    --with-ipv6 \
            $(CONFIGURE_OPTS)

build: config.status
	$(MAKE) build

build-stamp:
	dh_testdir
	touch $@

clean:
	dh_testdir
	dh_testroot
	rm -f build-stamp
	[ ! -f Makefile ] || $(MAKE) clean

ifneq "$(wildcard /usr/share/misc/config.sub)" ""
		rm -f config.sub
endif
ifneq "$(wildcard /usr/share/misc/config.guess)" ""
		rm -f config.guess
endif
	dh_clean

install:
	dh_testdir
	dh_testroot
	dh_prep
	dh_installdirs
	dh_install
	
	install -m644 debian/nginx.ufw.profile debian/nginx/etc/ufw/applications.d/nginx

binary-indep:

binary-arch: install
	dh_testdir
	dh_testroot
	dh_installchangelogs CHANGES
	dh_installdocs
	dh_installinit -r --no-start
	dh_installman debian/nginx.1
	dh_installlogrotate
	dh_link
	dh_strip --dbg-package=nginx-dbg
	dh_compress
	dh_fixperms
	dh_installdeb
	dh_shlibdeps
	dh_gencontrol
	dh_md5sums
	dh_builddeb

binary: binary-indep binary-arch

.PHONY: build clean binary-indep binary-arch binary install
```Perhaps I should explain what it is I'm trying to do.  I want to download a tarball from the Nginx site and build a deb, using Ubuntu's rules file as a template, and customize that.

---

