---
title: "Software Center depends on Gnome-Keyring?"
date: 2011-06-30
forum: The Cafe
---

### Post by Warpnow on 2011-06-30
What's up with this?

---

### Post by cariboo on 2011-06-30
I don't see anything in the software-center properties, where gnome-keyring is a dependency.

See [here]("http://packages.ubuntu.com/natty/software-center")

---

### Post by Tibuda on 2011-06-30
> **cariboo907 said:**
> I don't see anything in the software-center properties, where gnome-keyring is a dependency.

See [here]("http://packages.ubuntu.com/natty/software-center")

maybe it is a dependency of a dependency of a dependency of a dependency

[IMG]http://t2.gstatic.com/images?q=tbn:ANd9GcRLKJHDEwRUcIcFKAqAcOqqCVW00DSXzkvSdJpl0MX-0xE3hqihww&t=1[/IMG]

---

### Post by Bachstelze on 2011-06-30
> **Tibuda said:**
> maybe it is a dependency of a dependency of a dependency of a dependency

[IMG]http://t2.gstatic.com/images?q=tbn:ANd9GcRLKJHDEwRUcIcFKAqAcOqqCVW00DSXzkvSdJpl0MX-0xE3hqihww&t=1[/IMG]

Line 1193

```
firas@wakaba ~ % apt-rdepends software-center | nl               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
     1	software-center
     2	  Depends: app-install-data (>= 0.4.0)
     3	  Depends: aptdaemon (>= 0.31)
     4	  Depends: gconf2 (>= 2.28.1-2)
     5	  Depends: gnome-menus
     6	  Depends: humanity-icon-theme
     7	  Depends: policykit-1
     8	  Depends: policykit-1-gnome
     9	  Depends: policykit-1-kde
    10	  Depends: python
    11	  Depends: python-apt (>= 0.7.93.1)
    12	  Depends: python-aptdaemon (>= 0.31+bzr493)
    13	  Depends: python-aptdaemon-gtk
    14	  Depends: python-central (>= 0.6.11)
    15	  Depends: python-dbus
    16	  Depends: python-debian (>= 0.1.15)
    17	  Depends: python-gconf
    18	  Depends: python-gmenu
    19	  Depends: python-gtk2
    20	  Depends: python-lazr.restfulclient
    21	  Depends: python-webkit
    22	  Depends: python-xapian
    23	  Depends: python-xdg
    24	  Depends: ubuntu-sso-client (>= 0.99.6)
    25	app-install-data
    26	aptdaemon
    27	  Depends: python (>= 2.5)
    28	  Depends: python-aptdaemon (= 0.31+bzr506-0ubuntu2)
    29	python
    30	  Depends: python-minimal (= 2.5.2-0ubuntu1)
    31	  Depends: python2.5 (>= 2.5.2)
    32	python-minimal
    33	  Depends: dpkg (>= 1.13.20)
    34	  Depends: python2.5-minimal (>= 2.5.2)
    35	dpkg
    36	  PreDepends: coreutils (>= 5.93-1)
    37	  PreDepends: libc6 (>= 2.7-1)
    38	  PreDepends: lzma
    39	coreutils
    40	  PreDepends: libacl1 (>= 2.2.11-1)
    41	  PreDepends: libc6 (>= 2.4)
    42	  PreDepends: libselinux1
    43	libacl1
    44	  Depends: libattr1 (>= 2.4.4-1)
    45	  Depends: libc6 (>= 2.6.1-1)
    46	libattr1
    47	  Depends: libc6 (>= 2.6.1-1)
    48	libc6
    49	  Depends: libgcc1
    50	libgcc1
    51	  Depends: gcc-4.2-base (= 4.2.3-2ubuntu7)
    52	  Depends: libc6 (>= 2.7-1)
    53	gcc-4.2-base
    54	libselinux1
    55	  Depends: libc6 (>= 2.7-1)
    56	lzma
    57	  Depends: libc6 (>= 2.7-1)
    58	  Depends: libgcc1 (>= 1:4.2.1)
    59	  Depends: libstdc++6 (>= 4.2.1)
    60	libstdc++6
    61	  Depends: gcc-4.2-base (= 4.2.3-2ubuntu7)
    62	  Depends: libc6 (>= 2.7-1)
    63	  Depends: libgcc1 (>= 1:4.1.1-21)
    64	python2.5-minimal
    65	  Depends: libc6 (>= 2.4)
    66	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
    67	zlib1g
    68	  Depends: libc6 (>= 2.6.1-1)
    69	python2.5
    70	  Depends: libbz2-1.0
    71	  Depends: libc6 (>= 2.4)
    72	  Depends: libdb4.6
    73	  Depends: libncursesw5 (>= 5.6+20071006-3)
    74	  Depends: libreadline5 (>= 5.2)
    75	  Depends: libsqlite3-0 (>= 3.4.2)
    76	  Depends: libssl0.9.8 (>= 0.9.8f-1)
    77	  Depends: mime-support
    78	  Depends: python2.5-minimal (= 2.5.2-2ubuntu4)
    79	libbz2-1.0
    80	  Depends: libc6 (>= 2.7-1)
    81	libdb4.6
    82	  Depends: libc6 (>= 2.7-1)
    83	libncursesw5
    84	  Depends: libc6 (>= 2.7-1)
    85	libreadline5
    86	  Depends: libc6 (>= 2.6-1)
    87	  Depends: libncurses5 (>= 5.6)
    88	  Depends: readline-common
    89	libncurses5
    90	  Depends: libc6 (>= 2.7-1)
    91	readline-common
    92	libsqlite3-0
    93	  Depends: libc6 (>= 2.6.1-1)
    94	libssl0.9.8
    95	  Depends: debconf (>= 0.5)
    96	  Depends: debconf-2.0
    97	  Depends: libc6 (>= 2.4)
    98	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
    99	debconf
   100	  Depends: debconf-english
   101	  Depends: debconf-i18n
   102	  PreDepends: perl-base (>= 5.6.1-4)
   103	debconf-english
   104	  Depends: debconf
   105	debconf-i18n
   106	  Depends: debconf
   107	  Depends: liblocale-gettext-perl
   108	  Depends: libtext-charwidth-perl
   109	  Depends: libtext-iconv-perl
   110	  Depends: libtext-wrapi18n-perl
   111	liblocale-gettext-perl
   112	  Depends: libc6 (>= 2.2.5)
   113	  Depends: perl-base (>= 5.8.8-6)
   114	  Depends: perlapi-5.8.8
   115	perl-base
   116	  PreDepends: libc6 (>= 2.6.1-1)
   117	perlapi-5.8.8
   118	libtext-charwidth-perl
   119	  Depends: libc6 (>= 2.5-0ubuntu1)
   120	  Depends: perl-base (>= 5.8.8-7)
   121	  Depends: perlapi-5.8.8
   122	libtext-iconv-perl
   123	  Depends: libc6 (>= 2.4-1)
   124	  Depends: perl-base (>= 5.8.7-10ubuntu2)
   125	  Depends: perlapi-5.8.7
   126	perlapi-5.8.7
   127	libtext-wrapi18n-perl
   128	  Depends: libtext-charwidth-perl
   129	debconf-2.0
   130	mime-support
   131	python-aptdaemon
   132	  Depends: policykit-1
   133	  Depends: python (>= 2.6)
   134	  Depends: python-apt (>= 0.7.96.1ubuntu9)
   135	  Depends: python-central (>= 0.6.11)
   136	  Depends: python-gobject
   137	  Depends: python-software-properties
   138	policykit-1
   139	  Depends: consolekit
   140	  Depends: dbus
   141	  Depends: libc6 (>= 2.7)
   142	  Depends: libeggdbus-1-0 (>= 0.5)
   143	  Depends: libexpat1 (>= 1.95.8)
   144	  Depends: libglib2.0-0 (>= 2.21.4)
   145	  Depends: libpam0g (>= 0.99.7.1)
   146	  Depends: libpolkit-backend-1-0 (>= 0.94)
   147	  Depends: libpolkit-gobject-1-0 (>= 0.94)
   148	consolekit
   149	  Depends: dbus (>= 1.1.2)
   150	  Depends: libc6 (>= 2.7-1)
   151	  Depends: libck-connector0
   152	  Depends: libdbus-1-3 (>= 1.1.1)
   153	  Depends: libdbus-glib-1-2 (>= 0.74)
   154	  Depends: libglib2.0-0 (>= 2.16.0)
   155	  Depends: libx11-6
   156	dbus
   157	  Depends: adduser
   158	  Depends: consolekit (>= 0.2.3-3ubuntu2)
   159	  Depends: debianutils (>= 1.22.0)
   160	  Depends: libc6 (>= 2.7-1)
   161	  Depends: libdbus-1-3 (>= 0.94)
   162	  Depends: libexpat1 (>= 1.95.8)
   163	  Depends: libselinux1
   164	  Depends: lsb-base (>= 3.1)
   165	adduser
   166	  Depends: debconf
   167	  Depends: debconf-2.0
   168	  Depends: passwd (>= 1:4.0.12)
   169	  Depends: perl-base (>= 5.6.0)
   170	passwd
   171	  Depends: debianutils (>= 2.15.2)
   172	  Depends: libc6 (>= 2.7-1)
   173	  Depends: libpam-modules (>= 0.72-5)
   174	  Depends: libpam0g (>= 0.99.7.1)
   175	  Depends: libselinux1
   176	  Depends: login (>= 970502-1)
   177	debianutils
   178	  PreDepends: coreutils (>= 4.5.8-1)
   179	  PreDepends: libc6 (>= 2.7-1)
   180	  PreDepends: mktemp
   181	mktemp
   182	  PreDepends: libc6 (>= 2.7-1)
   183	libpam-modules
   184	  Depends: libc6 (>= 2.4)
   185	  Depends: libdb4.6
   186	  Depends: libpam0g (>= 0.99.7.1)
   187	  Depends: libselinux1
   188	libpam0g
   189	  Depends: debconf (>= 0.5)
   190	  Depends: debconf-2.0
   191	  Depends: libc6 (>= 2.4)
   192	  Depends: libpam-runtime
   193	libpam-runtime
   194	login
   195	  Depends: libpam-modules (>= 0.72-5)
   196	  PreDepends: libc6 (>= 2.7-1)
   197	  PreDepends: libpam-runtime (>= 0.76-14)
   198	  PreDepends: libpam0g (>= 0.99.7.1)
   199	libdbus-1-3
   200	  Depends: libc6 (>= 2.7-1)
   201	libexpat1
   202	  Depends: libc6 (>= 2.6.1-1)
   203	lsb-base
   204	  Depends: libncurses5
   205	  Depends: libpam0g
   206	  Depends: ncurses-bin
   207	  Depends: sed
   208	ncurses-bin
   209	  PreDepends: libc6 (>= 2.7-1)
   210	  PreDepends: libncurses5 (>= 5.6+20071006-3)
   211	sed
   212	  PreDepends: libc6 (>= 2.6.1-1)
   213	libck-connector0
   214	  Depends: libc6 (>= 2.7-1)
   215	  Depends: libdbus-1-3 (>= 1.1.1)
   216	libdbus-glib-1-2
   217	  Depends: libc6 (>= 2.2.5)
   218	  Depends: libdbus-1-3 (>= 1.1.1)
   219	  Depends: libglib2.0-0 (>= 2.16.0)
   220	libglib2.0-0
   221	  Depends: libc6 (>= 2.4)
   222	  Depends: libpcre3 (>= 7.4)
   223	  Depends: libselinux1
   224	libpcre3
   225	  Depends: libc6 (>= 2.7-1)
   226	libx11-6
   227	  Depends: libc6 (>= 2.7-1)
   228	  Depends: libx11-data
   229	  Depends: libxcb-xlib0
   230	  Depends: libxcb1
   231	  PreDepends: x11-common (>= 1:7.0.0)
   232	libx11-data
   233	  PreDepends: x11-common (>= 1:7.0.0)
   234	x11-common
   235	  Depends: debconf (>= 0.5)
   236	  Depends: debconf-2.0
   237	  Depends: debianutils (>= 1.13)
   238	  Depends: libc6 (>= 2.3)
   239	  Depends: lsb-base (>= 1.3-9ubuntu2)
   240	  PreDepends: debconf
   241	  PreDepends: debconf-2.0
   242	libxcb-xlib0
   243	  Depends: libc6 (>= 2.7-1)
   244	  Depends: libxcb1
   245	libxcb1
   246	  Depends: libc6 (>= 2.7-1)
   247	  Depends: libxau6
   248	  Depends: libxdmcp6
   249	libxau6
   250	  Depends: libc6 (>= 2.5-0ubuntu1)
   251	  Depends: x11-common
   252	libxdmcp6
   253	  Depends: libc6 (>= 2.5-0ubuntu1)
   254	  Depends: x11-common (>= 1:7.0.0)
   255	libeggdbus-1-0
   256	  Depends: libc6 (>= 2.2.5)
   257	  Depends: libdbus-1-3 (>= 1.0.2)
   258	  Depends: libdbus-glib-1-2 (>= 0.78)
   259	  Depends: libglib2.0-0 (>= 2.19.0)
   260	libpolkit-backend-1-0
   261	  Depends: libc6 (>= 2.4)
   262	  Depends: libeggdbus-1-0 (>= 0.5)
   263	  Depends: libexpat1 (>= 1.95.8)
   264	  Depends: libglib2.0-0 (>= 2.21.4)
   265	  Depends: libpolkit-gobject-1-0 (>= 0.95)
   266	libpolkit-gobject-1-0
   267	  Depends: libc6 (>= 2.4)
   268	  Depends: libeggdbus-1-0 (>= 0.5)
   269	  Depends: libglib2.0-0 (>= 2.24.0)
   270	python-apt
   271	  Depends: libapt-inst-libc6.7-6-1.1
   272	  Depends: libapt-pkg-libc6.7-6-4.6
   273	  Depends: libc6 (>= 2.4)
   274	  Depends: libgcc1 (>= 1:4.1.1-21)
   275	  Depends: libstdc++6 (>= 4.2.1-4)
   276	  Depends: lsb-release
   277	  Depends: python (<< 2.6)
   278	  Depends: python-central (>= 0.6.1)
   279	libapt-inst-libc6.7-6-1.1
   280	libapt-pkg-libc6.7-6-4.6
   281	lsb-release
   282	  Depends: python
   283	python-central
   284	  Depends: python (>= 2.4.3-10)
   285	python-gobject
   286	  Depends: libc6 (>= 2.4)
   287	  Depends: libffi4 (>= 4.1.1-21)
   288	  Depends: libglib2.0-0 (>= 2.16.0)
   289	  Depends: python (<< 2.6)
   290	  Depends: python-support (>= 0.7.1)
   291	libffi4
   292	  Depends: gcc-4.2-base (= 4.2.3-2ubuntu7)
   293	  Depends: libc6 (>= 2.7-1)
   294	python-support
   295	  Depends: python (>= 2.3)
   296	python-software-properties
   297	  Depends: iso-codes
   298	  Depends: lsb-release
   299	  Depends: python (>= 2.4)
   300	  Depends: python-apt (>= 0.6.20ubuntu16)
   301	  Depends: python-central (>= 0.5.62)
   302	  Depends: python-gnupginterface
   303	  Depends: unattended-upgrades
   304	iso-codes
   305	python-gnupginterface
   306	  Depends: gnupg (>= 1.2.1)
   307	  Depends: python-support (>= 0.2)
   308	gnupg
   309	  Depends: devfsd
   310	  Depends: gpgv
   311	  Depends: hurd
   312	  Depends: libbz2-1.0
   313	  Depends: libc6 (>= 2.7-1)
   314	  Depends: libcurl3-gnutls (>= 7.16.2-1)
   315	  Depends: libkrb53 (>= 1.6.dfsg.2)
   316	  Depends: libldap-2.4-2 (>= 2.4.7)
   317	  Depends: libreadline5 (>= 5.2)
   318	  Depends: libusb-0.1-4 (>= 2:0.1.12)
   319	  Depends: makedev (>= 2.3.1-13)
   320	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   321	devfsd
   322	gpgv
   323	  Depends: libc6 (>= 2.7-1)
   324	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   325	hurd
   326	libcurl3-gnutls
   327	  Depends: libc6 (>= 2.7-1)
   328	  Depends: libcomerr2 (>= 1.33-3)
   329	  Depends: libgnutls13 (>= 2.0.4-0)
   330	  Depends: libidn11 (>= 0.5.18)
   331	  Depends: libkrb53 (>= 1.6.dfsg.2)
   332	  Depends: libldap-2.4-2 (>= 2.4.7)
   333	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   334	libcomerr2
   335	  Depends: libc6 (>= 2.7-1)
   336	libgnutls13
   337	  Depends: libc6 (>= 2.7-1)
   338	  Depends: libgcrypt11 (>= 1.2.2)
   339	  Depends: liblzo2-2
   340	  Depends: libopencdk10 (>= 0.6.5)
   341	  Depends: libtasn1-3 (>= 0.3.4)
   342	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   343	libgcrypt11
   344	  Depends: libc6 (>= 2.6.1-1)
   345	  Depends: libgpg-error0 (>= 1.4)
   346	libgpg-error0
   347	  Depends: libc6 (>= 2.6.1-1)
   348	liblzo2-2
   349	  Depends: libc6 (>= 2.5-5)
   350	libopencdk10
   351	  Depends: libc6 (>= 2.6.1-1)
   352	  Depends: libgcrypt11 (>= 1.2.2)
   353	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   354	libtasn1-3
   355	  Depends: libc6 (>= 2.6.1-1)
   356	libidn11
   357	  Depends: libc6 (>= 2.6.1-1)
   358	libkrb53
   359	  Depends: libc6 (>= 2.7-1)
   360	  Depends: libcomerr2 (>= 1.33-3)
   361	  Depends: libkeyutils1
   362	libkeyutils1
   363	  Depends: libc6 (>= 2.6.1-1)
   364	libldap-2.4-2
   365	  Depends: libc6 (>= 2.4)
   366	  Depends: libgnutls13 (>= 2.0.4-0)
   367	  Depends: libsasl2-2
   368	libsasl2-2
   369	  Depends: libc6 (>= 2.4)
   370	  Depends: libdb4.6
   371	  Depends: libsasl2-modules (= 2.1.22.dfsg1-18ubuntu2)
   372	  Depends: libsasl2-modules-gssapi-heimdal (= 2.1.22.dfsg1-18ubuntu2)
   373	  Depends: libsasl2-modules-kerberos-heimdal (= 2.1.22.dfsg1-18ubuntu2)
   374	  Depends: libsasl2-modules-sql (= 2.1.22.dfsg1-18ubuntu2)
   375	libsasl2-modules
   376	  Depends: libc6 (>= 2.4)
   377	  Depends: libsasl2-2 (= 2.1.22.dfsg1-18ubuntu2)
   378	  Depends: libssl0.9.8 (>= 0.9.8f-1)
   379	libsasl2-modules-gssapi-heimdal
   380	  Depends: libasn1-8-heimdal
   381	  Depends: libc6 (>= 2.4)
   382	  Depends: libcomerr2 (>= 1.33-3)
   383	  Depends: libgssapi2-heimdal
   384	  Depends: libkrb5-22-heimdal
   385	  Depends: libroken18-heimdal
   386	  Depends: libsasl2-modules (= 2.1.22.dfsg1-18ubuntu2)
   387	  Depends: libssl0.9.8 (>= 0.9.8f-1)
   388	libasn1-8-heimdal
   389	  Depends: libc6 (>= 2.7-1)
   390	  Depends: libcomerr2 (>= 1.33-3)
   391	  Depends: libroken18-heimdal
   392	libroken18-heimdal
   393	  Depends: libc6 (>= 2.7-1)
   394	libgssapi2-heimdal
   395	  Depends: libasn1-8-heimdal
   396	  Depends: libc6 (>= 2.7-1)
   397	  Depends: libcomerr2 (>= 1.33-3)
   398	  Depends: libheimntlm0-heimdal
   399	  Depends: libkrb5-22-heimdal
   400	  Depends: libroken18-heimdal
   401	  Depends: libssl0.9.8 (>= 0.9.8f-1)
   402	libheimntlm0-heimdal
   403	  Depends: libc6 (>= 2.7-1)
   404	  Depends: libkrb5-22-heimdal
   405	  Depends: libroken18-heimdal
   406	libkrb5-22-heimdal
   407	  Depends: libasn1-8-heimdal
   408	  Depends: libc6 (>= 2.7-1)
   409	  Depends: libcomerr2 (>= 1.33-3)
   410	  Depends: libhx509-1-heimdal
   411	  Depends: libroken18-heimdal
   412	  Depends: libssl0.9.8 (>= 0.9.8f-1)
   413	libhx509-1-heimdal
   414	  Depends: libasn1-8-heimdal
   415	  Depends: libc6 (>= 2.7-1)
   416	  Depends: libcomerr2 (>= 1.33-3)
   417	  Depends: libroken18-heimdal
   418	  Depends: libssl0.9.8 (>= 0.9.8f-1)
   419	libsasl2-modules-kerberos-heimdal
   420	libsasl2-modules-sql
   421	  Depends: libc6 (>= 2.4)
   422	  Depends: libmysqlclient15off (>= 5.0.27-1)
   423	  Depends: libpq5 (>= 8.3~beta1)
   424	  Depends: libsasl2-modules (= 2.1.22.dfsg1-18ubuntu2)
   425	  Depends: libsqlite0 (>= 2.8.17)
   426	libmysqlclient15off
   427	  Depends: libc6 (>= 2.7-1)
   428	  Depends: mysql-common (>= 5.0.51a-3ubuntu5)
   429	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   430	mysql-common
   431	libpq5
   432	  Depends: libc6 (>= 2.7-1)
   433	  Depends: libcomerr2 (>= 1.33-3)
   434	  Depends: libkrb53 (>= 1.6.dfsg.2)
   435	  Depends: libldap-2.4-2 (>= 2.4.7)
   436	  Depends: libssl0.9.8 (>= 0.9.8f-1)
   437	libsqlite0
   438	  Depends: libc6 (>= 2.6.1-1)
   439	libusb-0.1-4
   440	  Depends: libc6 (>= 2.6.1-1)
   441	makedev
   442	  Depends: base-passwd (>= 3.0.4)
   443	base-passwd
   444	  Depends: libc6 (>= 2.6.1-1)
   445	unattended-upgrades
   446	  Depends: apt-utils
   447	  Depends: python
   448	  Depends: python-apt (>= 0.6.14ubuntu2)
   449	apt-utils
   450	  Depends: libapt-pkg-libc6.7-6-4.6
   451	  Depends: libc6 (>= 2.4)
   452	  Depends: libdb4.6
   453	  Depends: libgcc1 (>= 1:4.1.1-21)
   454	  Depends: libstdc++6 (>= 4.2.1-4)
   455	gconf2
   456	  Depends: gconf2-common (<< 2.23)
   457	  Depends: libc6 (>= 2.4)
   458	  Depends: libgconf2-4 (>= 2.13.5)
   459	  Depends: libxml2 (>= 2.6.27)
   460	  Depends: psmisc
   461	  Depends: python
   462	  PreDepends: libglib2.0-0 (>= 2.16.0)
   463	gconf2-common
   464	  Depends: ucf
   465	ucf
   466	  Depends: cdebconf
   467	  Depends: coreutils (>= 5.91)
   468	  Depends: debconf (>= 1.5.19)
   469	cdebconf
   470	  Depends: debconf
   471	  Depends: libatk1.0-0 (>= 1.13.2)
   472	  Depends: libc6 (>= 2.6.1-1)
   473	  Depends: libcairo2 (>= 1.4.0)
   474	  Depends: libdebian-installer4 (>= 0.52ubuntu1)
   475	  Depends: libfontconfig1 (>= 2.4.0)
   476	  Depends: libglib2.0-0 (>= 2.14.0)
   477	  Depends: libgtk2.0-0 (>= 2.12.0)
   478	  Depends: libnewt0.52
   479	  Depends: libpango1.0-0 (>= 1.18.2)
   480	  Depends: libslang2 (>= 2.0.7-1)
   481	  Depends: libtextwrap1
   482	  Depends: libx11-6
   483	  Depends: libxcomposite1 (>= 1:0.3-1)
   484	  Depends: libxcursor1 (>> 1.1.2)
   485	  Depends: libxdamage1 (>= 1:1.1)
   486	  Depends: libxext6
   487	  Depends: libxfixes3 (>= 1:4.0.1)
   488	  Depends: libxi6
   489	  Depends: libxinerama1
   490	  Depends: libxrandr2 (>= 2:1.2.0)
   491	  Depends: libxrender1
   492	libatk1.0-0
   493	  Depends: libc6 (>= 2.7-1)
   494	  Depends: libglib2.0-0 (>= 2.15.6)
   495	libcairo2
   496	  Depends: libc6 (>= 2.4)
   497	  Depends: libfontconfig1 (>= 2.4.0)
   498	  Depends: libfreetype6 (>= 2.3.5)
   499	  Depends: libgcc1 (>= 1:4.1.1-21)
   500	  Depends: libpixman-1-0 (>= 0.10.0)
   501	  Depends: libpng12-0 (>= 1.2.13-4)
   502	  Depends: libstdc++6
   503	  Depends: libx11-6
   504	  Depends: libxrender1
   505	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   506	libfontconfig1
   507	  Depends: fontconfig-config (= 2.5.0-2ubuntu3)
   508	  Depends: libc6 (>= 2.7-1)
   509	  Depends: libexpat1 (>= 1.95.8)
   510	  Depends: libfreetype6 (>= 2.3.5)
   511	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   512	fontconfig-config
   513	  Depends: debconf (>= 0.5)
   514	  Depends: debconf-2.0
   515	  Depends: gsfonts-x11
   516	  Depends: msttcorefonts
   517	  Depends: ttf-bitstream-vera
   518	  Depends: ttf-dejavu
   519	  Depends: ttf-freefont
   520	  Depends: ucf (>= 0.29)
   521	gsfonts-x11
   522	  Depends: gsfonts (>= 6.0-2)
   523	  Depends: xfonts-utils (>= 1:1.0.0-6)
   524	  Depends: xutils-dev
   525	gsfonts
   526	  Depends: defoma
   527	defoma
   528	  Depends: dialog
   529	  Depends: file
   530	  Depends: perl (>= 5.6.0-16)
   531	  Depends: whiptail
   532	dialog
   533	  Depends: debianutils (>= 1.6)
   534	  Depends: libc6 (>= 2.7-1)
   535	  Depends: libncursesw5 (>= 5.6+20071006-3)
   536	file
   537	  Depends: libc6 (>= 2.6.1-1)
   538	  Depends: libmagic1 (= 4.21-3)
   539	libmagic1
   540	  Depends: libc6 (>= 2.6.1-1)
   541	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   542	perl
   543	  Depends: libc6 (>= 2.6.1-1)
   544	  Depends: libdb4.6
   545	  Depends: libgdbm3
   546	  Depends: perl-base (= 5.8.8-12)
   547	  Depends: perl-modules (>= 5.8.8-12)
   548	libgdbm3
   549	  Depends: libc6 (>= 2.4-1)
   550	perl-modules
   551	  Depends: perl (>= 5.8.8-8)
   552	whiptail
   553	  Depends: libc6 (>= 2.7-1)
   554	  Depends: libnewt0.52 (>= 0.52.2)
   555	  Depends: libpopt0 (>= 1.10)
   556	  Depends: libslang2 (>= 2.0.7-1)
   557	libnewt0.52
   558	  Depends: libc6 (>= 2.7-1)
   559	  Depends: libslang2 (>= 2.0.7-1)
   560	libslang2
   561	  Depends: libc6 (>= 2.6.1-1)
   562	libpopt0
   563	  Depends: libc6 (>= 2.5-0ubuntu1)
   564	xfonts-utils
   565	  Depends: libc6 (>= 2.6.1-1)
   566	  Depends: libfontenc1
   567	  Depends: libfreetype6 (>= 2.3.5)
   568	  Depends: libxfont1
   569	  Depends: x11-common
   570	  Depends: xfonts-encodings
   571	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   572	libfontenc1
   573	  Depends: libc6 (>= 2.5-0ubuntu1)
   574	  Depends: x11-common
   575	  Depends: zlib1g (>= 1:1.2.1)
   576	libfreetype6
   577	  Depends: libc6 (>= 2.6-1)
   578	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   579	libxfont1
   580	  Depends: libc6 (>= 2.7-1)
   581	  Depends: libfontenc1
   582	  Depends: libfreetype6 (>= 2.3.5)
   583	  Depends: x11-common
   584	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   585	xfonts-encodings
   586	  Depends: x11-common
   587	xutils-dev
   588	  Depends: cpp
   589	  Depends: libc6 (>= 2.5-5)
   590	  PreDepends: x11-common (>= 1:7.0.0)
   591	cpp
   592	  Depends: cpp-4.2 (>= 4.2.3-1)
   593	cpp-4.2
   594	  Depends: gcc-4.2-base (= 4.2.3-2ubuntu7)
   595	  Depends: libc6 (>= 2.7-1)
   596	msttcorefonts
   597	  Depends: cabextract
   598	  Depends: cdebconf
   599	  Depends: debconf (>= 1.4.69)
   600	  Depends: defoma
   601	  Depends: wget
   602	  Depends: xfonts-utils
   603	cabextract
   604	  Depends: libc6 (>= 2.5-0ubuntu1)
   605	wget
   606	  Depends: libc6 (>= 2.5-5)
   607	  Depends: libssl0.9.8 (>= 0.9.8e-1)
   608	ttf-bitstream-vera
   609	  Depends: defoma
   610	ttf-dejavu
   611	  Depends: ttf-dejavu-core
   612	  Depends: ttf-dejavu-extra
   613	ttf-dejavu-core
   614	  Depends: defoma
   615	ttf-dejavu-extra
   616	  Depends: defoma
   617	  Depends: ttf-dejavu-core
   618	ttf-freefont
   619	  Depends: defoma
   620	libpixman-1-0
   621	  Depends: libc6 (>= 2.2.5)
   622	libpng12-0
   623	  Depends: libc6 (>= 2.6.1-1)
   624	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   625	libxrender1
   626	  Depends: libc6 (>= 2.6.1-1)
   627	  Depends: libx11-6
   628	libdebian-installer4
   629	  Depends: libc6 (>= 2.6.1-1)
   630	libgtk2.0-0
   631	  Depends: libatk1.0-0 (>= 1.20.0)
   632	  Depends: libc6 (>= 2.4)
   633	  Depends: libcairo2 (>= 1.6.0)
   634	  Depends: libcomerr2 (>= 1.33-3)
   635	  Depends: libcupsys2 (>= 1.3.4)
   636	  Depends: libfontconfig1 (>= 2.4.0)
   637	  Depends: libglib2.0-0 (>= 2.16.0)
   638	  Depends: libgnutls13 (>= 2.0.4-0)
   639	  Depends: libgtk2.0-common
   640	  Depends: libjpeg62
   641	  Depends: libkrb53 (>= 1.6.dfsg.2)
   642	  Depends: libpango1.0-0 (>= 1.20.1)
   643	  Depends: libpng12-0 (>= 1.2.13-4)
   644	  Depends: libtiff4
   645	  Depends: libx11-6
   646	  Depends: libxcomposite1 (>= 1:0.3-1)
   647	  Depends: libxcursor1 (>> 1.1.2)
   648	  Depends: libxdamage1 (>= 1:1.1)
   649	  Depends: libxext6
   650	  Depends: libxfixes3 (>= 1:4.0.1)
   651	  Depends: libxi6
   652	  Depends: libxinerama1
   653	  Depends: libxrandr2 (>= 2:1.2.0)
   654	  Depends: libxrender1
   655	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   656	libcupsys2
   657	  Depends: libc6 (>= 2.4)
   658	  Depends: libcomerr2 (>= 1.33-3)
   659	  Depends: libgnutls13 (>= 2.0.4-0)
   660	  Depends: libkrb53 (>= 1.6.dfsg.2)
   661	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   662	libgtk2.0-common
   663	libjpeg62
   664	  Depends: libc6 (>= 2.6-1)
   665	libpango1.0-0
   666	  Depends: libc6 (>= 2.4)
   667	  Depends: libcairo2 (>= 1.5.18)
   668	  Depends: libdatrie0 (>= 0.1.2)
   669	  Depends: libfontconfig1 (>= 2.4.0)
   670	  Depends: libfreetype6 (>= 2.3.5)
   671	  Depends: libglib2.0-0 (>= 2.16.0)
   672	  Depends: libpango1.0-common (>= 1.20.1-1)
   673	  Depends: libthai0 (>= 0.1.7)
   674	  Depends: libx11-6
   675	  Depends: libxft2 (>> 2.1.1)
   676	  Depends: libxrender1
   677	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   678	libdatrie0
   679	  Depends: libc6 (>= 2.6.1-1)
   680	libpango1.0-common
   681	  Depends: debconf
   682	  Depends: debconf-2.0
   683	  Depends: defoma (>= 0.11.1)
   684	  Depends: fontconfig (>= 2.1.91)
   685	fontconfig
   686	  Depends: defoma (>= 0.7.0)
   687	  Depends: fontconfig-config
   688	  Depends: libc6 (>= 2.7-1)
   689	  Depends: libexpat1 (>= 1.95.8)
   690	  Depends: libfontconfig1 (>= 2.4.0)
   691	  Depends: libfreetype6 (>= 2.3.5)
   692	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   693	libthai0
   694	  Depends: libc6 (>= 2.6-1)
   695	  Depends: libdatrie0
   696	  Depends: libthai-data
   697	libthai-data
   698	libxft2
   699	  Depends: libc6 (>= 2.4)
   700	  Depends: libfontconfig1 (>= 2.4.0)
   701	  Depends: libfreetype6 (>= 2.3.5)
   702	  Depends: libx11-6
   703	  Depends: libxrender1
   704	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   705	  PreDepends: x11-common (>= 1:7.0.0)
   706	libtiff4
   707	  Depends: libc6 (>= 2.7-1)
   708	  Depends: libjpeg62
   709	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   710	libxcomposite1
   711	  Depends: libc6 (>= 2.6.1-1)
   712	  Depends: libx11-6
   713	  Depends: libxext6
   714	  Depends: libxfixes3 (>= 1:4.0.1)
   715	  Depends: x11-common
   716	libxext6
   717	  Depends: libc6 (>= 2.6)
   718	  Depends: libx11-6
   719	  Depends: libxau6
   720	  Depends: x11-common
   721	libxfixes3
   722	  Depends: libc6 (>= 2.5-0ubuntu1)
   723	  Depends: libx11-6
   724	  PreDepends: x11-common (>= 1:7.0.0)
   725	libxcursor1
   726	  Depends: libc6 (>= 2.6.1-1)
   727	  Depends: libx11-6
   728	  Depends: libxfixes3 (>= 1:4.0.1)
   729	  Depends: libxrender1
   730	libxdamage1
   731	  Depends: libc6 (>= 2.5-0ubuntu1)
   732	  Depends: libx11-6
   733	  Depends: libxfixes3 (>= 1:4.0.1)
   734	  Depends: x11-common
   735	libxi6
   736	  Depends: libc6 (>= 2.6.1-1)
   737	  Depends: libx11-6
   738	  Depends: libxext6
   739	  Depends: x11-common
   740	libxinerama1
   741	  Depends: libc6 (>= 2.6)
   742	  Depends: libx11-6
   743	  Depends: libxext6
   744	  Depends: x11-common
   745	libxrandr2
   746	  Depends: libc6 (>= 2.6.1-1)
   747	  Depends: libx11-6
   748	  Depends: libxext6
   749	  Depends: libxrender1
   750	  Depends: x11-common
   751	libtextwrap1
   752	  Depends: libc6 (>= 2.4-1)
   753	libgconf2-4
   754	  Depends: gconf2-common (<< 2.23)
   755	  Depends: libc6 (>= 2.4)
   756	  Depends: libglib2.0-0 (>= 2.16.0)
   757	  Depends: libldap-2.4-2 (>= 2.4.7)
   758	  Depends: liborbit2 (>= 1:2.14.10)
   759	  Depends: libxml2 (>= 2.6.27)
   760	liborbit2
   761	  Depends: libc6 (>= 2.7-1)
   762	  Depends: libglib2.0-0 (>= 2.16.0)
   763	  Depends: libidl0
   764	libidl0
   765	  Depends: cpp
   766	  Depends: libc6 (>= 2.7-1)
   767	  Depends: libglib2.0-0 (>= 2.16.0)
   768	libxml2
   769	  Depends: libc6 (>= 2.7-1)
   770	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   771	psmisc
   772	  Depends: libc6 (>= 2.6.1-1)
   773	  Depends: libncurses5 (>= 5.6)
   774	gnome-menus
   775	  Depends: python (>= 2.3)
   776	  Depends: python-glade2
   777	  Depends: python-gmenu (= 2.22.1-0ubuntu1)
   778	python-glade2
   779	  Depends: libatk1.0-0 (>= 1.20.0)
   780	  Depends: libc6 (>= 2.7-1)
   781	  Depends: libcairo2 (>= 1.5.4)
   782	  Depends: libglade2-0 (>= 1:2.6.1)
   783	  Depends: libglib2.0-0 (>= 2.15.0)
   784	  Depends: libgtk2.0-0 (>= 2.12.0)
   785	  Depends: libpango1.0-0 (>= 1.19.2)
   786	  Depends: libxml2
   787	  Depends: python (>= 2.4)
   788	  Depends: python-gtk2 (= 2.12.1-0ubuntu1)
   789	  Depends: python-support (>= 0.7.1)
   790	libglade2-0
   791	  Depends: libatk1.0-0 (>= 1.13.2)
   792	  Depends: libc6 (>= 2.6)
   793	  Depends: libcairo2 (>= 1.4.0)
   794	  Depends: libfontconfig1 (>= 2.4.0)
   795	  Depends: libglib2.0-0 (>= 2.13.7)
   796	  Depends: libgtk2.0-0 (>= 2.11.6)
   797	  Depends: libpango1.0-0 (>= 1.17.5)
   798	  Depends: libx11-6
   799	  Depends: libxcomposite1 (>= 1:0.3-1)
   800	  Depends: libxcursor1 (>> 1.1.2)
   801	  Depends: libxdamage1 (>= 1:1.1)
   802	  Depends: libxext6
   803	  Depends: libxfixes3 (>= 1:4.0.1)
   804	  Depends: libxi6
   805	  Depends: libxinerama1
   806	  Depends: libxml2 (>= 2.6.29)
   807	  Depends: libxrandr2 (>= 2:1.2.0)
   808	  Depends: libxrender1
   809	python-gtk2
   810	  Depends: libatk1.0-0 (>= 1.20.0)
   811	  Depends: libc6 (>= 2.7-1)
   812	  Depends: libcairo2 (>= 1.5.4)
   813	  Depends: libglib2.0-0 (>= 2.15.0)
   814	  Depends: libgtk2.0-0 (>= 2.12.0)
   815	  Depends: libpango1.0-0 (>= 1.19.2)
   816	  Depends: python (>= 2.4)
   817	  Depends: python-cairo (>= 1.0.2-1.1)
   818	  Depends: python-gobject (>= 2.14)
   819	  Depends: python-numeric (>= 24.2-3)
   820	  Depends: python-support (>= 0.7.1)
   821	  Depends: python2.4-cairo
   822	  Depends: python2.4-gobject
   823	  Depends: python2.4-numeric
   824	  Depends: python2.5-cairo
   825	  Depends: python2.5-gobject
   826	  Depends: python2.5-numeric
   827	python-cairo
   828	  Depends: libc6 (>= 2.7-1)
   829	  Depends: libcairo2 (>= 1.5.12)
   830	  Depends: python (<< 2.6)
   831	  Depends: python-central (>= 0.5.62)
   832	python-numeric
   833	  Depends: libc6 (>= 2.7-1)
   834	  Depends: python (<< 2.6)
   835	  Depends: python-central (>= 0.5.62)
   836	python2.4-cairo
   837	python2.4-gobject
   838	python2.4-numeric
   839	python2.5-cairo
   840	python2.5-gobject
   841	python2.5-numeric
   842	python-gmenu
   843	  Depends: libc6 (>= 2.2.5)
   844	  Depends: libglib2.0-0 (>= 2.16.0)
   845	  Depends: libgnome-menu2 (>= 2.15.4)
   846	  Depends: python (<< 2.6)
   847	  Depends: python-central (>= 0.6.1)
   848	  Depends: python-gtk2
   849	libgnome-menu2
   850	  Depends: libc6 (>= 2.4)
   851	  Depends: libglib2.0-0 (>= 2.16.0)
   852	humanity-icon-theme
   853	  Depends: gnome-icon-theme
   854	  Depends: hicolor-icon-theme
   855	gnome-icon-theme
   856	  Depends: hicolor-icon-theme
   857	  Depends: librsvg2-common
   858	hicolor-icon-theme
   859	librsvg2-common
   860	  Depends: gtk2.0-binver-2.10.0
   861	  Depends: libc6 (>= 2.7-1)
   862	  Depends: libglib2.0-0 (>= 2.16.0)
   863	  Depends: libgtk2.0-0 (>= 2.12.0)
   864	  Depends: librsvg2-2 (= 2.22.2-2)
   865	gtk2.0-binver-2.10.0
   866	librsvg2-2
   867	  Depends: libc6 (>= 2.7-1)
   868	  Depends: libcairo2 (>= 1.5.12)
   869	  Depends: libcroco3 (>= 0.6.1)
   870	  Depends: libfontconfig1 (>= 2.4.0)
   871	  Depends: libfreetype6 (>= 2.3.5)
   872	  Depends: libglib2.0-0 (>= 2.16.0)
   873	  Depends: libgsf-1-114 (>= 1.14.7)
   874	  Depends: libgtk2.0-0 (>= 2.12.0)
   875	  Depends: libpango1.0-0 (>= 1.20.0)
   876	  Depends: libxml2 (>= 2.6.27)
   877	libcroco3
   878	  Depends: libc6 (>= 2.6)
   879	  Depends: libglib2.0-0 (>= 2.13.7)
   880	  Depends: libxml2 (>= 2.6.29)
   881	libgsf-1-114
   882	  Depends: libbz2-1.0
   883	  Depends: libc6 (>= 2.7-1)
   884	  Depends: libglib2.0-0 (>= 2.15.4)
   885	  Depends: libgsf-1-common (>= 1.14.7-2ubuntu1)
   886	  Depends: libxml2 (>= 2.6.27)
   887	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   888	libgsf-1-common
   889	policykit-1-gnome
   890	  Depends: libappindicator1 (>= 0.0.19)
   891	  Depends: libc6 (>= 2.2.5)
   892	  Depends: libdbus-glib-1-2 (>= 0.78)
   893	  Depends: libgdk-pixbuf2.0-0 (>= 2.21.6)
   894	  Depends: libglib2.0-0 (>= 2.24.0)
   895	  Depends: libgtk2.0-0 (>= 2.17.1)
   896	  Depends: libpolkit-agent-1-0 (>= 0.94)
   897	  Depends: libpolkit-gobject-1-0 (>= 0.94)
   898	  Depends: policykit-1
   899	libappindicator1
   900	  Depends: libatk1.0-0 (>= 1.29.3)
   901	  Depends: libc6 (>= 2.2.5)
   902	  Depends: libcairo2 (>= 1.2.4)
   903	  Depends: libdbus-1-3 (>= 1.0.2)
   904	  Depends: libdbus-glib-1-2 (>= 0.88)
   905	  Depends: libdbusmenu-glib1 (>= 0.3.12)
   906	  Depends: libdbusmenu-gtk1 (>= 0.3.12)
   907	  Depends: libfontconfig1 (>= 2.8.0)
   908	  Depends: libfreetype6 (>= 2.2.1)
   909	  Depends: libgdk-pixbuf2.0-0 (>= 2.21.6)
   910	  Depends: libglib2.0-0 (>= 2.16.0)
   911	  Depends: libgtk2.0-0 (>= 2.18.0)
   912	  Depends: libindicator1
   913	  Depends: libjson-glib-1.0-0
   914	  Depends: libpango1.0-0 (>= 1.14.0)
   915	  Depends: libpng12-0 (>= 1.2.13-4)
   916	libdbusmenu-glib1
   917	  Depends: libc6 (>= 2.2.5)
   918	  Depends: libdbus-1-3 (>= 1.0.2)
   919	  Depends: libdbus-glib-1-2 (>= 0.88)
   920	  Depends: libglib2.0-0 (>= 2.18.0)
   921	  Depends: libxml2 (>= 2.7.4)
   922	libdbusmenu-gtk1
   923	  Depends: libatk1.0-0 (>= 1.29.3)
   924	  Depends: libc6 (>= 2.2.5)
   925	  Depends: libcairo2 (>= 1.2.4)
   926	  Depends: libdbus-1-3 (>= 1.0.2)
   927	  Depends: libdbus-glib-1-2 (>= 0.78)
   928	  Depends: libdbusmenu-glib1 (>= 0.3.12)
   929	  Depends: libfontconfig1 (>= 2.8.0)
   930	  Depends: libfreetype6 (>= 2.2.1)
   931	  Depends: libgdk-pixbuf2.0-0 (>= 2.21.6)
   932	  Depends: libglib2.0-0 (>= 2.16.0)
   933	  Depends: libgtk2.0-0 (>= 2.16.0)
   934	  Depends: libpango1.0-0 (>= 1.14.0)
   935	  Depends: libpng12-0 (>= 1.2.13-4)
   936	  Depends: libxml2 (>= 2.6.27)
   937	libgdk-pixbuf2.0-0
   938	  Depends: libc6 (>= 2.11)
   939	  Depends: libglib2.0-0 (>= 2.25.9)
   940	  Depends: libjasper1 (>= 1.900.1)
   941	  Depends: libjpeg62
   942	  Depends: libpng12-0 (>= 1.2.13-4)
   943	  Depends: libtiff4
   944	  Depends: libx11-6
   945	  Depends: zlib1g (>= 1:1.1.4)
   946	libjasper1
   947	  Depends: libc6 (>= 2.5-0ubuntu1)
   948	  Depends: libjpeg62
   949	libindicator1
   950	  Depends: libatk1.0-0 (>= 1.29.3)
   951	  Depends: libc6 (>= 2.2.5)
   952	  Depends: libcairo2 (>= 1.2.4)
   953	  Depends: libdbus-1-3 (>= 1.0.2)
   954	  Depends: libdbus-glib-1-2 (>= 0.88)
   955	  Depends: libfontconfig1 (>= 2.8.0)
   956	  Depends: libfreetype6 (>= 2.2.1)
   957	  Depends: libgdk-pixbuf2.0-0 (>= 2.21.6)
   958	  Depends: libglib2.0-0 (>= 2.22)
   959	  Depends: libgtk2.0-0 (>= 2.18)
   960	  Depends: libpango1.0-0 (>= 1.14.0)
   961	  Depends: libpng12-0 (>= 1.2.13-4)
   962	libjson-glib-1.0-0
   963	  Depends: libc6 (>= 2.4)
   964	  Depends: libglib2.0-0 (>= 2.16.0)
   965	libpolkit-agent-1-0
   966	  Depends: libc6 (>= 2.2.5)
   967	  Depends: libeggdbus-1-0 (>= 0.5)
   968	  Depends: libexpat1 (>= 1.95.8)
   969	  Depends: libglib2.0-0 (>= 2.21.4)
   970	  Depends: libpolkit-gobject-1-0 (>= 0.94)
   971	policykit-1-kde
   972	python-aptdaemon-gtk
   973	  Depends: python (>= 2.6)
   974	  Depends: python-aptdaemon (= 0.31+bzr506-0ubuntu2)
   975	  Depends: python-central (>= 0.6.11)
   976	  Depends: python-gtk2
   977	  Depends: python-vte
   978	python-vte
   979	  Depends: libatk1.0-0 (>= 1.20.0)
   980	  Depends: libc6 (>= 2.7-1)
   981	  Depends: libcairo2 (>= 1.5.12)
   982	  Depends: libffi4
   983	  Depends: libfontconfig1 (>= 2.4.0)
   984	  Depends: libfreetype6 (>= 2.3.5)
   985	  Depends: libglib2.0-0 (>= 2.12.0)
   986	  Depends: libgtk2.0-0 (>= 2.12.0)
   987	  Depends: libice6 (>= 1:1.0.0)
   988	  Depends: libncurses5 (>= 5.6+20071006-3)
   989	  Depends: libpango1.0-0 (>= 1.20.0)
   990	  Depends: libsm6
   991	  Depends: libvte9 (>= 1:0.16.9)
   992	  Depends: libx11-6
   993	  Depends: libxft2 (>> 2.1.1)
   994	  Depends: python (<< 2.6)
   995	  Depends: python-gtk2
   996	  Depends: python-support (>= 0.7.1)
   997	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
   998	libice6
   999	  Depends: libc6 (>= 2.6.1-1)
  1000	  Depends: x11-common
  1001	libsm6
  1002	  Depends: libc6 (>= 2.5-5)
  1003	  Depends: libice6 (>= 1:1.0.0)
  1004	  Depends: x11-common
  1005	libvte9
  1006	  Depends: libatk1.0-0 (>= 1.20.0)
  1007	  Depends: libc6 (>= 2.7-1)
  1008	  Depends: libcairo2 (>= 1.5.12)
  1009	  Depends: libfontconfig1 (>= 2.4.0)
  1010	  Depends: libfreetype6 (>= 2.3.5)
  1011	  Depends: libglib2.0-0 (>= 2.16.0)
  1012	  Depends: libgtk2.0-0 (>= 2.12.0)
  1013	  Depends: libice6 (>= 1:1.0.0)
  1014	  Depends: libncurses5 (>= 5.6+20071006-3)
  1015	  Depends: libpango1.0-0 (>= 1.20.0)
  1016	  Depends: libpixman-1-0 (>= 0.9.4-2)
  1017	  Depends: libpng12-0 (>= 1.2.13-4)
  1018	  Depends: libsm6
  1019	  Depends: libvte-common
  1020	  Depends: libx11-6
  1021	  Depends: libxft2 (>> 2.1.1)
  1022	  Depends: libxrender1
  1023	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
  1024	libvte-common
  1025	python-dbus
  1026	  Depends: libc6 (>= 2.7-1)
  1027	  Depends: libdbus-1-3 (>= 1.1.1)
  1028	  Depends: libdbus-glib-1-2 (>= 0.74)
  1029	  Depends: libglib2.0-0 (>= 2.15.6)
  1030	  Depends: python (<< 2.6)
  1031	  Depends: python-support (>= 0.7.1)
  1032	python-debian
  1033	  Depends: python (>= 2.4)
  1034	  Depends: python-support (>= 0.7.1)
  1035	python-gconf
  1036	  Depends: libc6 (>= 2.7-1)
  1037	  Depends: libgconf2-4 (>= 2.13.5)
  1038	  Depends: libglib2.0-0 (>= 2.15.6)
  1039	  Depends: python (<< 2.6)
  1040	  Depends: python-pyorbit (>= 2.0.1-4)
  1041	  Depends: python-support (>= 0.7.1)
  1042	python-pyorbit
  1043	  Depends: libc6 (>= 2.6.1-1)
  1044	  Depends: libglib2.0-0 (>= 2.14.0)
  1045	  Depends: libidl0
  1046	  Depends: liborbit2 (>= 1:2.14.8)
  1047	  Depends: python (>= 2.4)
  1048	  Depends: python-support (>= 0.7.1)
  1049	python-lazr.restfulclient
  1050	  Depends: python (>= 2.6)
  1051	  Depends: python-central (>= 0.6.11)
  1052	  Depends: python-httplib2
  1053	  Depends: python-pkg-resources
  1054	  Depends: python-simplejson
  1055	  Depends: python-wadllib (>= 1.1.4)
  1056	  Depends: python-zope.interface
  1057	python-httplib2
  1058	  Depends: python (>= 2.5)
  1059	  Depends: python-support (>= 0.3.4)
  1060	  Depends: python2.5
  1061	python-pkg-resources
  1062	  Depends: python (<< 2.6)
  1063	  Depends: python-central (>= 0.6.1)
  1064	python-simplejson
  1065	  Depends: libc6 (>= 2.6.1-1)
  1066	  Depends: python (>= 2.4)
  1067	  Depends: python-support (>= 0.7.1)
  1068	python-wadllib
  1069	  Depends: python (>= 2.4)
  1070	  Depends: python-lazr.uri
  1071	  Depends: python-simplejson
  1072	  Depends: python-support (>= 0.90.0)
  1073	python-lazr.uri
  1074	  Depends: python (>= 2.6)
  1075	  Depends: python-central (>= 0.6.11)
  1076	  Depends: python-pkg-resources
  1077	python-zope.interface
  1078	  Depends: libc6 (>= 2.2.5)
  1079	  Depends: python (>= 2.6)
  1080	  Depends: python-central (>= 0.6.11)
  1081	  Depends: python-pkg-resources
  1082	python-webkit
  1083	  Depends: libatk1.0-0 (>= 1.29.3)
  1084	  Depends: libc6 (>= 2.2.5)
  1085	  Depends: libcairo2 (>= 1.2.4)
  1086	  Depends: libfontconfig1 (>= 2.8.0)
  1087	  Depends: libfreetype6 (>= 2.2.1)
  1088	  Depends: libgdk-pixbuf2.0-0 (>= 2.21.6)
  1089	  Depends: libglib2.0-0 (>= 2.16.0)
  1090	  Depends: libgtk2.0-0 (>= 2.10.0)
  1091	  Depends: libpango1.0-0 (>= 1.14.0)
  1092	  Depends: libsoup2.4-1 (>= 2.4.0)
  1093	  Depends: libwebkit-1.0-2 (>= 1.1.14)
  1094	  Depends: libxml2 (>= 2.6.27)
  1095	  Depends: libxslt1.1 (>= 1.1.18)
  1096	  Depends: python (>= 2.6)
  1097	  Depends: python-gtk2
  1098	  Depends: python-support (>= 0.90.0)
  1099	libsoup2.4-1
  1100	  Depends: libc6 (>= 2.4)
  1101	  Depends: libgcrypt11 (>= 1.2.2)
  1102	  Depends: libglib2.0-0 (>= 2.16.0)
  1103	  Depends: libgnutls13 (>= 2.0.4-0)
  1104	  Depends: libxml2 (>= 2.6.27)
  1105	libwebkit-1.0-2
  1106	  Depends: libatk1.0-0 (>= 1.29.3)
  1107	  Depends: libc6 (>= 2.11)
  1108	  Depends: libcairo2 (>= 1.6.0)
  1109	  Depends: libenchant1c2a (>= 1.6)
  1110	  Depends: libfontconfig1 (>= 2.8.0)
  1111	  Depends: libfreetype6 (>= 2.2.1)
  1112	  Depends: libgail18 (>= 1.18.0)
  1113	  Depends: libgdk-pixbuf2.0-0 (>= 2.21.6)
  1114	  Depends: libglib2.0-0 (>= 2.24.0)
  1115	  Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.23)
  1116	  Depends: libgstreamer0.10-0 (>= 0.10.20)
  1117	  Depends: libgtk2.0-0 (>= 2.21.6)
  1118	  Depends: libicu42 (>= 4.2-1)
  1119	  Depends: libjpeg62
  1120	  Depends: libpango1.0-0 (>= 1.22.0)
  1121	  Depends: libpng12-0 (>= 1.2.13-4)
  1122	  Depends: libsoup2.4-1 (>= 2.29.90)
  1123	  Depends: libsqlite3-0 (>= 3.7.2)
  1124	  Depends: libstdc++6 (>= 4.1.1)
  1125	  Depends: libwebkit-1.0-common (>= 1.2.4)
  1126	  Depends: libxml2 (>= 2.7.4)
  1127	  Depends: libxslt1.1 (>= 1.1.25)
  1128	  Depends: libxt6
  1129	libenchant1c2a
  1130	  Depends: libaspell15 (>= 0.60)
  1131	  Depends: libc6 (>= 2.7-1)
  1132	  Depends: libgcc1 (>= 1:4.2.1)
  1133	  Depends: libglib2.0-0 (>= 2.14.0)
  1134	  Depends: libhunspell-1.1-0 (>= 1.1.6-1)
  1135	  Depends: libstdc++6 (>= 4.2.1)
  1136	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
  1137	libaspell15
  1138	  Depends: libc6 (>= 2.7-1)
  1139	  Depends: libgcc1
  1140	  Depends: libstdc++6 (>= 4.1.1-21)
  1141	libhunspell-1.1-0
  1142	  Depends: libc6 (>= 2.6.1-1)
  1143	  Depends: libgcc1 (>= 1:4.2.1)
  1144	  Depends: libstdc++6 (>= 4.2.1)
  1145	libgail18
  1146	  Depends: libatk1.0-0 (>= 1.20.0)
  1147	  Depends: libc6 (>= 2.2.5)
  1148	  Depends: libglib2.0-0 (>= 2.16.0)
  1149	  Depends: libgtk2.0-0 (>= 2.12.0)
  1150	  Depends: libpango1.0-0 (>= 1.20.0)
  1151	libgstreamer-plugins-base0.10-0
  1152	  Depends: libc6 (>= 2.7-1)
  1153	  Depends: libglib2.0-0 (>= 2.16.0)
  1154	  Depends: libgstreamer0.10-0 (>= 0.10.18)
  1155	libgstreamer0.10-0
  1156	  Depends: libc6 (>= 2.7-1)
  1157	  Depends: libglib2.0-0 (>= 2.16.0)
  1158	  Depends: libxml2 (>= 2.6.27)
  1159	libicu42
  1160	  Depends: libc6 (>= 2.7)
  1161	  Depends: libgcc1 (>= 1:4.1.1)
  1162	  Depends: libstdc++6 (>= 4.1.1)
  1163	libwebkit-1.0-common
  1164	libxslt1.1
  1165	  Depends: libc6 (>= 2.6.1-1)
  1166	  Depends: libgcrypt11 (>= 1.2.2)
  1167	  Depends: libxml2 (>= 2.6.29)
  1168	libxt6
  1169	  Depends: libc6 (>= 2.5-5)
  1170	  Depends: libice6 (>= 1:1.0.0)
  1171	  Depends: libsm6
  1172	  Depends: libx11-6
  1173	  PreDepends: x11-common (>= 1:7.0.0)
  1174	python-xapian
  1175	  Depends: libc6 (>= 2.7-1)
  1176	  Depends: libgcc1 (>= 1:4.1.1-21)
  1177	  Depends: libstdc++6 (>= 4.1.1-21)
  1178	  Depends: libxapian15
  1179	  Depends: python (<< 2.6)
  1180	  Depends: python-central (>= 0.6.1)
  1181	libxapian15
  1182	  Depends: libc6 (>= 2.7-1)
  1183	  Depends: libgcc1 (>= 1:4.1.1-21)
  1184	  Depends: libstdc++6 (>= 4.2.1-4)
  1185	  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)
  1186	python-xdg
  1187	  Depends: python (>= 2.3)
  1188	  Depends: python-support (>= 0.7.1)
  1189	ubuntu-sso-client
  1190	  Depends: dpkg (>= 1.15.7.2)
  1191	  Depends: python (>= 2.6)
  1192	  Depends: python-dbus
  1193	  Depends: python-gnomekeyring
  1194	  Depends: python-gtk2
  1195	  Depends: python-lazr.restfulclient
  1196	  Depends: python-oauth
  1197	  Depends: python-support (>= 0.90.0)
  1198	  Depends: python-twisted-core
  1199	  Depends: python-twisted-web
  1200	  Depends: python-webkit
  1201	  Depends: python-xdg
  1202	python-gnomekeyring
  1203	  Depends: libc6 (>= 2.4)
  1204	  Depends: libglib2.0-0 (>= 2.12.0)
  1205	  Depends: libgnome-keyring0 (>= 2.20.3)
  1206	  Depends: python (>= 2.6)
  1207	  Depends: python-gtk2
  1208	  Depends: python-support (>= 0.90.0)
  1209	libgnome-keyring0
  1210	  Depends: libc6 (>= 2.4)
  1211	  Depends: libdbus-1-3 (>= 1.1.1)
  1212	  Depends: libglib2.0-0 (>= 2.16.0)
  1213	python-oauth
  1214	  Depends: python (>= 2.4)
  1215	  Depends: python-central (>= 0.6.7)
  1216	python-twisted-core
  1217	  Depends: python (>= 2.3.5-9)
  1218	  Depends: python-central (>= 0.5.62)
  1219	  Depends: python-twisted-bin (>= 2.5.0-2build2)
  1220	  Depends: python-zopeinterface (>= 3.2.1-3)
  1221	python-twisted-bin
  1222	  Depends: libc6 (>= 2.7-1)
  1223	  Depends: python (<< 2.6)
  1224	python-zopeinterface
  1225	  Depends: libc6 (>= 2.2.5)
  1226	  Depends: python (<< 2.6)
  1227	  Depends: python-central (>= 0.6.1)
  1228	python-twisted-web
  1229	  Depends: python
  1230	  Depends: python-central (>= 0.5.62)
  1231	  Depends: python-twisted-core (>= 2.5)

```

---

