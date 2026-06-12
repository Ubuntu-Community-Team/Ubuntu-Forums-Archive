---
title: "Multimedia dependencies for Apache Solr on Ubuntu Server 10.04"
date: 2011-05-25
forum: Server Platforms
---

### Post by JPorter on 2011-05-25
I'm about to install Solr on one of our test servers running Ubuntu Server 10.04.1, and the dependency lists for both solr-jetty and solr-tomcat have me very confused.

Here's what I get back from the dependency tree for solr-jetty:
```
ant
ant-gcj
ant-optional
ant-optional-gcj
ca-certificates-java
defoma
fontconfig
gcj-4.4-base
gcj-4.4-jre-lib
hicolor-icon-theme
icedtea-6-jre-cacao
java-common
jetty
jsvc
libaccess-bridge-java
libaccess-bridge-java-jni
libasound2
libatk1.0-0
libatk1.0-data
libavahi-client3
libavahi-common-data
libavahi-common3
libbcel-java
libcairo2
libcommons-beanutils-java
libcommons-codec-java
libcommons-collections-java
libcommons-collections3-java
libcommons-compress-java
libcommons-csv-java
libcommons-daemon-java
libcommons-dbcp-java
libcommons-digester-java
libcommons-fileupload-java
libcommons-httpclient-java
libcommons-io-java
libcommons-logging-java
libcommons-pool-java
libcups2
libdatrie1
libdb-je-java
libdb4.7-java
libdb4.7-java-gcj
libdirectfb-1.2-0
libecj-java
libflac8
libfontenc1
libgcj-bc
libgcj-common
libgcj10
libgif4
libgnuinet-java
libgnujaf-java
libgnumail-java
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common
libice6
libicu4j-java
libjasper1
libjaxp1.3-java
libjetty-extra
libjetty-extra-java
libjetty-java
libjetty-java-doc
libjline-java
libjtidy-java
liblcms1
liblog4j1.2-java
liblucene2-java
libmx4j-java
libnspr4-0d
libnss3-1d
libogg0
libpango1.0-0
libpango1.0-common
libpixman-1-0
libpulse0
libregexp-java
libservlet2.5-java
libslf4j-java
libsm6
libsndfile1
libsysfs2
libthai-data
libthai0
libtiff4
libtomcat6-java
libts-0.0-0
libvorbis0a
libvorbisenc2
libxcb-render-util0
libxcb-render0
libxcomposite1
libxcursor1
libxdamage1
libxerces2-java
libxfixes3
libxfont1
libxft2
libxi6
libxinerama1
libxml-commons-external-java
libxrandr2
libxrender1
libxtst6
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
solr-common
solr-jetty
tsconf
ttf-dejavu-extra
tzdata-java
x-ttcidfont-conf
xfonts-encodings
xfonts-utils
```

What's the deal with all the multimedia and fonts stuff in there?  Come on, [FONT="Courier New"]hicolor-icon-theme[/FONT]? This is a headless server, I don't understand why Jetty or Tomcat or the underlying OpenJDK packages would require packages like [FONT="Courier New"]libasound2[/FONT], [FONT="Courier New"]libflac8[/FONT], [FONT="Courier New"]libvorbisenc2[/FONT] or any of the other multimedia packages in there. The font packages also have me confused.

To make matters more confusing, the dependency list for the same package on my Ubuntu 11.04 desktop machine doesn't seem to have the same multimedia "needs".

Has anyone else run into this, and is there a workaround?

---

### Post by JPorter on 2011-05-31
Has anyone else run into these desktop-oriented dependencies when installing OpenJDK?

---

### Post by tpfeiffer on 2011-06-08
Hi!

> **JPorter said:**
> Has anyone else run into these desktop-oriented dependencies when installing OpenJDK?

The problem seems to be as follows: solr-common depends on java6-runtime-headless (note: headless) and libcommons-csv-java, among others. now libcommons-csv-java depends on openjdk-6-jre or java2-runtime (note: no headless). This in turn pulls libaccess-bridge-java-jni -> libgtk2.0-0 -> libxinerama1 and many other packages that are unavoidable for your Solr server ;-)

I guess that one should file a bug against libcommons-csv-java. A dependency on java6-runtime-headless should be enough...

Tobias

PS. check [https://bugs.launchpad.net/server-papercuts/+bug/598017](https://bugs.launchpad.net/server-papercuts/+bug/598017)

---

### Post by JPorter on 2011-06-21
Thanks tpfeiffer, I added to the bug report and managed to manually work-around using the maverick package for libcommons-csv-java.

This is why the community is great... excellent work sir.

---

