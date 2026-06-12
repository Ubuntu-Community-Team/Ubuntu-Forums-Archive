---
title: "eclipse offline installation for ubuntu"
date: 2008-08-11
forum: Repositories &amp; Backports
---

### Post by ivanceras on 2008-08-11
Hi everyone,

Its been a week trying to install eclipse in ubuntu with no success. Does anybody here knows how to install eclipse for ubuntu without using an active internet connection(I mean a downloadable installer). I've tried eclipse.org eclipse for linux, but it throws errors "Widget disposed too early..etc". I also tried downloading the packages in "packages.ubuntu.com" repositories, but it has a lot of dependencies. I think its time to listen to experts.

Can anyone help me with this?, Or can anyone give a link of a functional eclipse installer for ubuntu?

Thanks in advance,
ivanceras

---

### Post by zj3t3mju on 2008-08-11
you can try this tool [http://wapt-get.googlecode.com/](http://wapt-get.googlecode.com/)
or direct link(for hardy, create by wapt-get, not test yet, VN host)
```
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/java-common/java-common_0.28ubuntu3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/e/ecj/libecj-java_3.3.0+0728-5_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/gcj-4.2-base_4.2.3-2ubuntu6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcc-defaults/libgcj-common_4.2.3-1ubuntu3_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/libgcj8-1_4.2.3-2ubuntu6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/gij-4.2_4.2.3-2ubuntu6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/libgcj8-jar_4.2.3-2ubuntu6_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/e/ecj/ecj_3.3.0+0728-5_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcc-defaults/libgcj-bc_4.2.3-1ubuntu3_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/e/ecj/libecj-java-gcj_3.3.0+0728-5_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/e/ecj/ecj-gcj_3.3.0+0728-5_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/libgcj8-1-awt_4.2.3-2ubuntu6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/gappletviewer-4.2_4.2.3-2ubuntu6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-16.30_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu3_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3.3.dfsg-7ubuntu1_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/libgcj8-dev_4.2.3-2ubuntu6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcj-4.2/gcj-4.2_4.2.3-2ubuntu6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.16.6ubuntu3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/h/html2text/html2text_1.3.2a-3build2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gettext/gettext_0.17-2ubuntu1_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.35.0+20060710.1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.10_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/d/debhelper/debhelper_6.0.4ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gcc-defaults/gij_4.2.3-1ubuntu3_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/f/fastjar/fastjar_0.95-1_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/jakarta-log4j/liblog4j1.2-java_1.2.15-2_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/libr/libregexp-java/libregexp-java_1.4-4_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/b/bcel/libbcel-java_5.2-3ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/libm/libmx4j-java/libmx4j-java_3.0.1-3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/java-gcj-compat/java-gcj-compat-headless_1.0.77-2ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/java-gcj-compat/java-gcj-compat_1.0.77-2ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/a/antlr/antlr_2.7.6-10_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gjdoc/gjdoc_0.7.8-6_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/java-gcj-compat/java-gcj-compat-dev_1.0.77-2ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/libj/libjaxp1.3-java/libjaxp1.3-java_1.3.04-2_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/libx/libxerces2-java/libxerces2-java_2.9.0-1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/a/ant/ant_1.7.0-3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/a/ant/ant-optional_1.7.0-3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/e/eclipse/libswt3.2-gtk-jni_3.2.2-5ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/e/eclipse/libswt3.2-gtk-java_3.2.2-5ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/e/eclipse/eclipse-rcp_3.2.2-5ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/jsch/libjsch-java_0.1.37-2_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/l/lucene/liblucene-java_1.4.3.dfsg-3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/l/lucene/liblucene-java-doc_1.4.3.dfsg-3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/k/kaffe/kaffe-common_1.1.8-3ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.2+dfsg-1ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/k/kaffe/kaffe-pthreads_1.1.8-3ubuntu1_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/k/kaffe/kaffe_1.1.8-3ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/libc/libcommons-collections3-java/libcommons-collections3-java_3.1a-3.1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/c/commons-pool/libcommons-pool-java_1.3-1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/libc/libcommons-collections-java/libcommons-collections-java_2.1.1-8_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/libc/libcommons-dbcp-java/libcommons-dbcp-java_1.2.2-1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/libs/libservlet2.4-java/libservlet2.4-java_5.0.30-6ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/libc/libcommons-el-java/libcommons-el-java_1.0-4_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/javax-servletapi2.3/libservlet2.3-java_4.0-10_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/libc/libcommons-logging-java/libcommons-logging-java_1.1-1ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/libc/libcommons-launcher-java/libcommons-launcher-java_1.1-3_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/c/commons-beanutils/libcommons-beanutils-java_1.8.0~beta-1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/libc/libcommons-digester-java/libcommons-digester-java_1.8-1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/libc/libcommons-modeler-java/libcommons-modeler-java_2.0.1-4_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/t/tomcat5.5/libtomcat5.5-java_5.5.25-5ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/e/eclipse/eclipse-platform_3.2.2-5ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/main/j/junit/junit_3.8.2-1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/j/junit4/junit4_4.3.1-2_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/e/eclipse/eclipse-jdt_3.2.2-5ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/e/eclipse/eclipse-pde_3.2.2-5ubuntu2_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/x/xulrunner/libmozjs0d_1.8.1.13+nobinonly-0ubuntu1_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/x/xulrunner/libxul-common_1.8.1.13+nobinonly-0ubuntu1_all.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/x/xulrunner/libxul0d_1.8.1.13+nobinonly-0ubuntu1_i386.deb
http://www.oss-hcm.gov.vn/ubuntu/pool/universe/e/eclipse/eclipse_3.2.2-5ubuntu2_i386.deb

```
after download install by ```
sudo dpkg -i *.deb
```
if error occur, run it again

---

