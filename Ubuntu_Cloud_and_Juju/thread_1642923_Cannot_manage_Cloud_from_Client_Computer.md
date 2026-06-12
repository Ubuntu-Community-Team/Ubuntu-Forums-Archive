---
title: "Cannot manage Cloud from Client Computer"
date: 2010-12-11
forum: Ubuntu Cloud and Juju
---

### Post by indrasuryatama on 2010-12-11
Hi , i have setup my UEC,
1. Front End(CC,CLC,Walrus,S3) (Ubuntu server 10.04)
2. Node (NC) (Ubuntu server 10.04)
3. Client (Ubuntu Desktop 10.04)
 and it goes well when i control it from my front end(CLC,CC,Walrus,S3) .
On UEC Begginers guide, it said that we can manage the cloud from a  Client host (Ubuntu Desktop 10.04) , but i still can't sent my  enviroment variabel well
 i set the enviroment variable by typing ". ~/.euca/uecarc" on  terminal, but when it tried to do "euca-describe-availability-zones  verbose" i got this following error:
 Warning: failed to parse error message from AWS: :1:0: syntax error
EC2ResponseError: 403 Forbidden
Failure: 403 Forbidden
 but i can ping my virtual machine from cloud control host computer.
 what should i do?


 NB:
this is my eucarc file
EUCA_KEY_DIR=$(dirname $(readlink -f ${BASH_SOURCE}))
export S3_URL=http://192.168.10.121:8773/services/Walrus
export EC2_URL=http://192.168.10.121:8773/services/Eucalyptus
export EC2_PRIVATE_KEY=${EUCA_KEY_DIR}/euca2-admin-b37dc790-pk.pem
export EC2_CERT=${EUCA_KEY_DIR}/euca2-admin-b37dc790-cert.pem
export EC2_JVM_ARGS=-Djavax.net.ssl.trustStore=${EUCA_KEY_DIR}/jssecacerts
export EUCALYPTUS_CERT=${EUCA_KEY_DIR}/cloud-cert.pem
export EC2_ACCESS_KEY='WKy3rMzOWPouVOxK1p3Ar1C2uRBwa2FBXnCw'
export EC2_SECRET_KEY='4KYgRVgkfsF8VcrcfWutG9mkvfmlTR0rGYw'
# This is a bogus value; Eucalyptus does not need this but client tools do.
export EC2_USER_ID='000100729354'
alias ec2-bundle-image="ec2-bundle-image --cert ${EC2_CERT} --privatekey ${EC2_$
alias ec2-upload-bundle="ec2-upload-bundle -a ${EC2_ACCESS_KEY} -s ${EC2_SECRET$


 this is when i do command "printenv | grep EC2"
EC2_JVM_ARGS=-Djavax.net.ssl.trustStore=/home/indra/.euca/jssecacerts
EC2_SECRET_KEY=4KYgRVgkfsF8VcrcfWutG9mkvfmlTR0rGYw
EC2_USER_ID=000100729354
EC2_URL=http://192.168.10.121:8773/services/Eucalyptus
EC2_ACCESS_KEY=WKy3rMzOWPouVOxK1p3Ar1C2uRBwa2FBXnCw
EC2_PRIVATE_KEY=/home/indra/.euca/euca2-admin-b37dc790-pk.pem
EC2_CERT=/home/indra/.euca/euca2-admin-b37dc790-cert.pem


 when i do euca-describe-availability-zones verbose , is still got this following error
 Warning: failed to parse error message from AWS: :1:0: syntax error
 EC2ResponseError: 403 Forbidden
Failure: 403 Forbidden
 Regards
 Indra Suryatama

---

### Post by raymdt on 2010-12-11
Hi suryatama,
first sorry for my poor english.
Do you have a firewall in you subnet?
Please try **telnet 192.168.10.121 8773**  on the client (Ubuntu Desktop)  plus
**ls -al**  in your .euca's directory on the client  and post the result here.
regards

raymdt

---

### Post by indrasuryatama on 2010-12-11
> **raymdt said:**
> Hi suryatama,
first sorry for my poor english.
Do you have a firewall in you subnet?
Please try **telnet 192.168.10.121 8773**  on the client (Ubuntu Desktop)  plus
**ls -al**  in your .euca's directory on the client  and post the result here.
regards

raymdt

i dont use any firewall on my subnet,
i can ssh'ing my front end (CLC) 

here is the result of ls-al from .euca
drwx------  2 indra indra 4096 2010-12-09 13:08 .
drwxr-xr-x 30 indra indra 4096 2010-12-11 15:44 ..
-rw-r--r--  1 indra indra 1257 2010-11-29 12:25 cloud-cert.pem
-rw-r--r--  1 indra indra 1269 2010-11-29 12:25 euca2-admin-b37dc790-cert.pem
-rw-r--r--  1 indra indra 1679 2010-11-29 12:25 euca2-admin-b37dc790-pk.pem
-rw-r--r--  1 indra indra  935 2010-11-29 12:25 eucarc
lrwxrwxrwx  1 indra indra    6 2010-12-09 13:08 .eucarc -> eucarc
-rw-r--r--  1 indra indra  954 2010-11-29 12:25 jssecacerts
-rw-r--r--  1 indra indra 5059 2010-11-29 12:26 mycreds.zip

what should i do?

---

### Post by kim0 on 2010-12-11
He did ask you to run
telnet 192.168.10.121 8773

---

### Post by indrasuryatama on 2010-12-11
> **kim0 said:**
> He did ask you to run
telnet 192.168.10.121 8773

what is the use of telnet?

it said trying 192.168.10.121..
Connected to 192.168.10.121.
Escape charcter is '^]'.

and then , what i'am suppose to do ?

---

### Post by kim0 on 2010-12-13
Hi,
Well telnet confirms whether or not you really can connect on a network level to that port. So when it says "Connected to 192.168.10.121" that is good since it means that port really is reachable to you

However, now we're left not sure why you're getting the original error though! I think Synchronizing the time of your euca2ools machine with that of your front end may help. Can you try that. If it doesn't work still, you're probably hitting some bug. Could you try finding any hints in any log files and posting to the mailing list

---

### Post by indrasuryatama on 2010-12-14
> **kim0 said:**
> Hi,
Well telnet confirms whether or not you really can connect on a network level to that port. So when it says "Connected to 192.168.10.121" that is good since it means that port really is reachable to you

However, now we're left not sure why you're getting the original error though! I think Synchronizing the time of your euca2ools machine with that of your front end may help. Can you try that. If it doesn't work still, you're probably hitting some bug. Could you try finding any hints in any log files and posting to the mailing list

i have sync my time using NTP, 
the server goes to my front end...
i'll try to finding any hint...
whats the log should i post ? i'll try to ask on mailing list.. but no one know about that error too

---

### Post by kim0 on 2010-12-14
You need to sync clock on the client PC as well (plus CLC, and NCs). On the CLC, you may find error logs in /var/log/eucalyptus

---

### Post by indrasuryatama on 2010-12-14
ok, i'll try and i'll keep you informed...

---

### Post by indrasuryatama on 2010-12-15
> **kim0 said:**
> You need to sync clock on the client PC as well (plus CLC, and NCs). On the CLC, you may find error logs in /var/log/eucalyptus

i have sync my time using NTP, but it failed..
i also try to find the error on my CLC (/var/log/eucalyptus[) 
but i cant found that directory on my front end....
so what should i do?
the error is still same

---

### Post by kim0 on 2010-12-15
sigh too bad ... not sure how to further debug this. The log directory should exist though! something is fishy.

---

### Post by raymdt on 2010-12-15
Hi indrasuryatama

This is very interesting.
Please can you post  the result of **locate eucalyptus** on your CLC Machine (The same machine where eucalyptus-cc eucalyptus-walrus eucalyptus-sc are installed)

Have you tried using another client ????

---

### Post by indrasuryatama on 2010-12-15
> **kim0 said:**
> sigh too bad ... not sure how to further debug this. The log directory should exist though! something is fishy.
i couldnt find it T____T, this problem make me frustated.. almost a month i struggle with this problem

> **raymdt said:**
> Hi indrasuryatama

This is very interesting.
Please can you post  the result of **locate eucalyptus** on your CLC Machine (The same machine where eucalyptus-cc eucalyptus-walrus eucalyptus-sc are installed)

Have you tried using another client ????
i'll give you the result tommorow , because its already midnight on my time. and my private cloud was setup on faculty lab.
tx for your concern

---

### Post by indrasuryatama on 2010-12-15
double post >_<

---

### Post by raymdt on 2010-12-15
I think that your installation is broken. You could try to repair it but you can save a lot of time by  reinstalling CLC, CC, SC and Walrus then use #euca_conf --register......  to register them + NC

you can save your eucalyptus.conf "and eucalyptus.local.conf"

```


apt-get remove --purge eucalyptus* 


#verify that the /var/lib/eucalyptus  directory is empty

#then  install CLC, CC, SC, Walrus. Synchronize the clock and register CC SC Walrus and NC.

apt-get update && apt-get upgrade

apt-get install  eucalyptus-cloud eucalyptus-cc eucalyptus-sc eucalyptus-walrus



```

---

### Post by indrasuryatama on 2010-12-15
> **raymdt said:**
> I think that your installation is broken. You could try to repair it but you can save a lot of time by  reinstalling CLC, CC, SC and Walrus then use #euca_conf --register......  to register them + NC

you can save your eucalyptus.conf "and eucalyptus.local.conf"

```


apt-get remove --purge eucalyptus* 


#verify that the /var/lib/eucalyptus  directory is empty

#then  install CLC, CC, SC, Walrus. Synchronize the clock and register CC SC Walrus and NC.

apt-get update && apt-get upgrade

apt-get install  eucalyptus-cloud eucalyptus-cc eucalyptus-sc eucalyptus-walrus



```

just for your information, i install CLC,CC,SC,Walrus on the same machine.... (Front End), am i still need to reinstall the CC,CLC, SC, Walrus

and this is the output from locate eucalyptus, i can find the log on "/var/log/eucalyptus"

/etc/eucalyptus
/etc/eucalyptus/axis2
/etc/eucalyptus/cloud.d
/etc/eucalyptus/eucalyptus-cc.conf
/etc/eucalyptus/eucalyptus-ipaddr.conf
/etc/eucalyptus/eucalyptus-sc.conf
/etc/eucalyptus/eucalyptus-version
/etc/eucalyptus/eucalyptus.conf
/etc/eucalyptus/eucalyptus.local.conf
/etc/eucalyptus/eucalyptus.local.conf.bak
/etc/eucalyptus/httpd.conf
/etc/eucalyptus/preseed
/etc/eucalyptus/vtunall.conf.template
/etc/eucalyptus/wrappers.conf
/etc/eucalyptus/axis2/axis2.xml
/etc/eucalyptus/axis2/lib
/etc/eucalyptus/axis2/modules
/etc/eucalyptus/axis2/services
/etc/eucalyptus/cloud.d/eucalyptus-web-default.properties
/etc/eucalyptus/cloud.d/eucalyptus-web.properties
/etc/eucalyptus/cloud.d/gwt-web.xml
/etc/eucalyptus/cloud.d/scripts
/etc/eucalyptus/cloud.d/security.policy
/etc/eucalyptus/cloud.d/www
/etc/eucalyptus/cloud.d/www/admin.xml
/etc/eucalyptus/cloud.d/www/preseed.xml
/etc/init/eucalyptus-cc-publication.conf
/etc/init/eucalyptus-cc.conf
/etc/init/eucalyptus-cloud-publication.conf
/etc/init/eucalyptus-cloud.conf
/etc/init/eucalyptus-network.conf
/etc/init/eucalyptus-sc-publication.conf
/etc/init/eucalyptus-sc.conf
/etc/init/eucalyptus-walrus-publication.conf
/etc/init/eucalyptus-walrus.conf
/etc/init/eucalyptus.conf
/etc/init.d/eucalyptus
/etc/init.d/eucalyptus-cc
/etc/init.d/eucalyptus-cc-publication
/etc/init.d/eucalyptus-cloud
/etc/init.d/eucalyptus-cloud-publication
/etc/init.d/eucalyptus-network
/etc/init.d/eucalyptus-sc
/etc/init.d/eucalyptus-sc-publication
/etc/init.d/eucalyptus-walrus
/etc/init.d/eucalyptus-walrus-publication
/etc/update-motd.d/15-eucalyptus-url
/usr/lib/eucalyptus
/usr/lib/axis2/services/EucalyptusCC/eucalyptus_cc.wsdl
/usr/lib/axis2/services/EucalyptusGL/eucalyptus_gl.wsdl
/usr/lib/eucalyptus/cloud.d
/usr/lib/eucalyptus/euca_rootwrap
/usr/lib/eucalyptus/euca_upgrade
/usr/lib/eucalyptus/liblvm2control.so
/usr/lib/eucalyptus/cloud.d/scripts
/usr/lib/eucalyptus/cloud.d/scripts/Import_150.groovy
/usr/lib/eucalyptus/cloud.d/scripts/Import_152.groovy
/usr/lib/eucalyptus/cloud.d/scripts/Import_161.groovy
/usr/lib/eucalyptus/cloud.d/scripts/LeastFullFirst.groovy
/usr/lib/eucalyptus/cloud.d/scripts/after_database.groovy
/usr/lib/eucalyptus/cloud.d/scripts/after_persistence.groovy
/usr/lib/eucalyptus/cloud.d/scripts/before_database.groovy
/usr/lib/eucalyptus/cloud.d/scripts/caches.groovy
/usr/lib/eucalyptus/cloud.d/scripts/channels.groovy
/usr/lib/eucalyptus/cloud.d/scripts/describe_nodes.groovy
/usr/lib/eucalyptus/cloud.d/scripts/entities.groovy
/usr/lib/eucalyptus/cloud.d/scripts/pools.groovy
/usr/lib/eucalyptus/cloud.d/scripts/startup.groovy
/usr/lib/eucalyptus/cloud.d/scripts/vmstate.groovy
/usr/lib/python2.6/dist-packages/landscape/manager/eucalyptus.py
/usr/lib/python2.6/dist-packages/landscape/manager/eucalyptus.pyc
/usr/sbin/eucalyptus-cloud
/usr/share/eucalyptus
/usr/share/apport/package-hooks/source_eucalyptus.py
/usr/share/doc/eucalyptus-cc
/usr/share/doc/eucalyptus-cloud
/usr/share/doc/eucalyptus-common
/usr/share/doc/eucalyptus-gl
/usr/share/doc/eucalyptus-java-common
/usr/share/doc/eucalyptus-sc
/usr/share/doc/eucalyptus-walrus
/usr/share/doc/libeucalyptus-commons-ext-java
/usr/share/doc/eucalyptus-cc/README
/usr/share/doc/eucalyptus-cc/changelog.Debian.gz
/usr/share/doc/eucalyptus-cc/changelog.gz
/usr/share/doc/eucalyptus-cc/copyright
/usr/share/doc/eucalyptus-cloud/README
/usr/share/doc/eucalyptus-cloud/changelog.Debian.gz
/usr/share/doc/eucalyptus-cloud/changelog.gz
/usr/share/doc/eucalyptus-cloud/copyright
/usr/share/doc/eucalyptus-common/README
/usr/share/doc/eucalyptus-common/changelog.Debian.gz
/usr/share/doc/eucalyptus-common/changelog.gz
/usr/share/doc/eucalyptus-common/copyright
/usr/share/doc/eucalyptus-gl/README
/usr/share/doc/eucalyptus-gl/changelog.Debian.gz
/usr/share/doc/eucalyptus-gl/changelog.gz
/usr/share/doc/eucalyptus-gl/copyright
/usr/share/doc/eucalyptus-java-common/README
/usr/share/doc/eucalyptus-java-common/changelog.Debian.gz
/usr/share/doc/eucalyptus-java-common/changelog.gz
/usr/share/doc/eucalyptus-java-common/copyright
/usr/share/doc/eucalyptus-sc/README
/usr/share/doc/eucalyptus-sc/changelog.Debian.gz
/usr/share/doc/eucalyptus-sc/changelog.gz
/usr/share/doc/eucalyptus-sc/copyright
/usr/share/doc/eucalyptus-walrus/README
/usr/share/doc/eucalyptus-walrus/changelog.Debian.gz
/usr/share/doc/eucalyptus-walrus/changelog.gz
/usr/share/doc/eucalyptus-walrus/copyright
/usr/share/doc/libeucalyptus-commons-ext-java/changelog.Debian.gz
/usr/share/doc/libeucalyptus-commons-ext-java/copyright
/usr/share/eucalyptus/activation.jar
/usr/share/eucalyptus/add_key.pl
/usr/share/eucalyptus/antlr.jar
/usr/share/eucalyptus/antlr3-3.0.1+dfsg.jar
/usr/share/eucalyptus/asm2.jar
/usr/share/eucalyptus/axiom-api.jar
/usr/share/eucalyptus/axiom-dom.jar
/usr/share/eucalyptus/axiom-impl.jar
/usr/share/eucalyptus/backport-util-concurrent.jar
/usr/share/eucalyptus/bcel.jar
/usr/share/eucalyptus/bcprov.jar
/usr/share/eucalyptus/bsf.jar
/usr/share/eucalyptus/cglib.jar
/usr/share/eucalyptus/chgrp-dhcpd
/usr/share/eucalyptus/chmod-dhcpd
/usr/share/eucalyptus/commons-beanutils.jar
/usr/share/eucalyptus/commons-cli.jar
/usr/share/eucalyptus/commons-codec.jar
/usr/share/eucalyptus/commons-collections3.jar
/usr/share/eucalyptus/commons-discovery.jar
/usr/share/eucalyptus/commons-fileupload.jar
/usr/share/eucalyptus/commons-httpclient.jar
/usr/share/eucalyptus/commons-io.jar
/usr/share/eucalyptus/commons-jxpath.jar
/usr/share/eucalyptus/commons-lang.jar
/usr/share/eucalyptus/commons-logging-adapters.jar
/usr/share/eucalyptus/commons-logging-api.jar
/usr/share/eucalyptus/commons-logging.jar
/usr/share/eucalyptus/commons-pool.jar
/usr/share/eucalyptus/dd-lv
/usr/share/eucalyptus/dnsjava.jar
/usr/share/eucalyptus/dom4j.jar
/usr/share/eucalyptus/drools-compiler.jar
/usr/share/eucalyptus/drools-core.jar
/usr/share/eucalyptus/ecj.jar
/usr/share/eucalyptus/el-api-2.1.jar
/usr/share/eucalyptus/euca_ipt
/usr/share/eucalyptus/eucalyptus-auth-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-cloud-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-clustermgr-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-commons-ext-0.4.jar
/usr/share/eucalyptus/eucalyptus-config-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-core-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-db-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-dns-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-groupmgr-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-imagemgr-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-interface-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-keymgr-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-msgs-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-storage-common-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-storagecontroller-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-walrus-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-ws-1.6.2.jar
/usr/share/eucalyptus/eucalyptus-www-1.6.2.jar
/usr/share/eucalyptus/excalibur-logkit.jar
/usr/share/eucalyptus/ezmorph.jar
/usr/share/eucalyptus/geronimo-ejb-3.0-spec.jar
/usr/share/eucalyptus/geronimo-interceptor-3.0-spec.jar
/usr/share/eucalyptus/geronimo-j2ee-connector-1.5-spec.jar
/usr/share/eucalyptus/geronimo-jacc-1.1-spec.jar
/usr/share/eucalyptus/geronimo-jms-1.1-spec.jar
/usr/share/eucalyptus/geronimo-jpa-3.0-spec.jar
/usr/share/eucalyptus/geronimo-jta-1.0.1b-spec.jar
/usr/share/eucalyptus/gnumail-providers.jar
/usr/share/eucalyptus/gnumail.jar
/usr/share/eucalyptus/google-collections.jar
/usr/share/eucalyptus/groovy.jar
/usr/share/eucalyptus/gwt-servlet.jar
/usr/share/eucalyptus/gwt-user.jar
/usr/share/eucalyptus/hsqldb.jar
/usr/share/eucalyptus/hsqldbutil.jar
/usr/share/eucalyptus/inetlib.jar
/usr/share/eucalyptus/janino.jar
/usr/share/eucalyptus/javassist.jar
/usr/share/eucalyptus/jaxen.jar
/usr/share/eucalyptus/jaxp-1.3.jar
/usr/share/eucalyptus/jcl-over-slf4j.jar
/usr/share/eucalyptus/jetty-sslengine.jar
/usr/share/eucalyptus/jetty-util.jar
/usr/share/eucalyptus/jetty.jar
/usr/share/eucalyptus/jibx-bind.jar
/usr/share/eucalyptus/jibx-extras.jar
/usr/share/eucalyptus/jibx-run.jar
/usr/share/eucalyptus/json-lib.jar
/usr/share/eucalyptus/jug-asl.jar
/usr/share/eucalyptus/jul-to-slf4j.jar
/usr/share/eucalyptus/junit.jar
/usr/share/eucalyptus/log4j-1.2.jar
/usr/share/eucalyptus/modprobe-aoe
/usr/share/eucalyptus/mvel.jar
/usr/share/eucalyptus/netty.jar
/usr/share/eucalyptus/openjdk-crypto.jar
/usr/share/eucalyptus/populate_arp.pl
/usr/share/eucalyptus/proxool.jar
/usr/share/eucalyptus/regexp.jar
/usr/share/eucalyptus/registration
/usr/share/eucalyptus/serializer.jar
/usr/share/eucalyptus/servlet-api-2.5.jar
/usr/share/eucalyptus/slf4j-api.jar
/usr/share/eucalyptus/slf4j-log4j12.jar
/usr/share/eucalyptus/wsdl4j.jar
/usr/share/eucalyptus/wss4j.jar
/usr/share/eucalyptus/wstx-lgpl.jar
/usr/share/eucalyptus/xalan2.jar
/usr/share/eucalyptus/xercesImpl.jar
/usr/share/eucalyptus/xml-security.jar
/usr/share/eucalyptus/xom.jar
/usr/share/eucalyptus/xpp3.jar
/usr/share/eucalyptus/registration/cluster
/usr/share/eucalyptus/registration/common
/usr/share/eucalyptus/registration/node
/usr/share/eucalyptus/registration/storage
/usr/share/eucalyptus/registration/walrus
/usr/share/man/man5/eucalyptus.conf.5.gz
/usr/share/man/man5/eucalyptus.local.conf.5.gz
/usr/share/pyshared/landscape/manager/eucalyptus.py
/var/lib/eucalyptus
/var/lib/dpkg/info/eucalyptus-cc.conffiles
/var/lib/dpkg/info/eucalyptus-cc.config
/var/lib/dpkg/info/eucalyptus-cc.list
/var/lib/dpkg/info/eucalyptus-cc.md5sums
/var/lib/dpkg/info/eucalyptus-cc.postinst
/var/lib/dpkg/info/eucalyptus-cc.postrm
/var/lib/dpkg/info/eucalyptus-cc.preinst
/var/lib/dpkg/info/eucalyptus-cc.prerm
/var/lib/dpkg/info/eucalyptus-cc.templates
/var/lib/dpkg/info/eucalyptus-cloud.conffiles
/var/lib/dpkg/info/eucalyptus-cloud.list
/var/lib/dpkg/info/eucalyptus-cloud.md5sums
/var/lib/dpkg/info/eucalyptus-cloud.postinst
/var/lib/dpkg/info/eucalyptus-cloud.postrm
/var/lib/dpkg/info/eucalyptus-cloud.preinst
/var/lib/dpkg/info/eucalyptus-cloud.prerm
/var/lib/dpkg/info/eucalyptus-common.conffiles
/var/lib/dpkg/info/eucalyptus-common.list
/var/lib/dpkg/info/eucalyptus-common.md5sums
/var/lib/dpkg/info/eucalyptus-common.postinst
/var/lib/dpkg/info/eucalyptus-common.postrm
/var/lib/dpkg/info/eucalyptus-common.preinst
/var/lib/dpkg/info/eucalyptus-common.prerm
/var/lib/dpkg/info/eucalyptus-gl.list
/var/lib/dpkg/info/eucalyptus-gl.md5sums
/var/lib/dpkg/info/eucalyptus-java-common.conffiles
/var/lib/dpkg/info/eucalyptus-java-common.list
/var/lib/dpkg/info/eucalyptus-java-common.md5sums
/var/lib/dpkg/info/eucalyptus-java-common.postinst
/var/lib/dpkg/info/eucalyptus-java-common.preinst
/var/lib/dpkg/info/eucalyptus-sc.conffiles
/var/lib/dpkg/info/eucalyptus-sc.config
/var/lib/dpkg/info/eucalyptus-sc.list
/var/lib/dpkg/info/eucalyptus-sc.md5sums
/var/lib/dpkg/info/eucalyptus-sc.postinst
/var/lib/dpkg/info/eucalyptus-sc.postrm
/var/lib/dpkg/info/eucalyptus-sc.preinst
/var/lib/dpkg/info/eucalyptus-sc.prerm
/var/lib/dpkg/info/eucalyptus-sc.templates
/var/lib/dpkg/info/eucalyptus-walrus.conffiles
/var/lib/dpkg/info/eucalyptus-walrus.list
/var/lib/dpkg/info/eucalyptus-walrus.md5sums
/var/lib/dpkg/info/eucalyptus-walrus.postinst
/var/lib/dpkg/info/eucalyptus-walrus.postrm
/var/lib/dpkg/info/eucalyptus-walrus.preinst
/var/lib/dpkg/info/eucalyptus-walrus.prerm
/var/lib/dpkg/info/libeucalyptus-commons-ext-java.list
/var/lib/dpkg/info/libeucalyptus-commons-ext-java.md5sums
/var/lib/eucalyptus/.ssh
/var/lib/eucalyptus/CC
/var/lib/eucalyptus/bukkits
/var/lib/eucalyptus/db
/var/lib/eucalyptus/keys
/var/lib/eucalyptus/modules
/var/lib/eucalyptus/nodes.list
/var/lib/eucalyptus/volumes
/var/lib/eucalyptus/webapps
/var/lib/eucalyptus/.ssh/id_rsa
/var/lib/eucalyptus/.ssh/id_rsa.pub
/var/lib/eucalyptus/webapps/root.war
/var/lib/update-rc.d/eucalyptus
/var/lib/update-rc.d/eucalyptus-cc
/var/lib/update-rc.d/eucalyptus-cc-publication
/var/lib/update-rc.d/eucalyptus-cloud
/var/lib/update-rc.d/eucalyptus-cloud-publication
/var/lib/update-rc.d/eucalyptus-network
/var/lib/update-rc.d/eucalyptus-sc
/var/lib/update-rc.d/eucalyptus-sc-publication
/var/lib/update-rc.d/eucalyptus-walrus
/var/lib/update-rc.d/eucalyptus-walrus-publication
/var/log/eucalyptus

---

### Post by raymdt on 2010-12-16
Hey Indra,
i don't understand your last Post.
Have you already removed and reinstalled CLC,CC,SC and Walrus or is this output from your old installation?

These files are missing.......

```

/var/log/eucalyptus/axis2c.log
/var/log/eucalyptus/cc.log
/var/log/eucalyptus/cc.log.0
/var/log/eucalyptus/cc.log.1
/var/log/eucalyptus/cc.log.2
/var/log/eucalyptus/cc.log.3
/var/log/eucalyptus/cc.log.4
/var/log/eucalyptus/cloud-debug.log
/var/log/eucalyptus/cloud-error.log
/var/log/eucalyptus/cloud-exhaust.log
/var/log/eucalyptus/cloud-output.log
/var/log/eucalyptus/httpd-cc_error_log
/var/log/eucalyptus/jetty-request-******log
/var/log/eucalyptus/jetty-request-******.log
/var/log/eucalyptus/registration.log
/var/log/eucalyptus/sc-stats.log
/var/log/eucalyptus/walrus-stats.log


```

---

### Post by indrasuryatama on 2010-12-16
> **raymdt said:**
> Hey Indra,
i don't understand your last Post.
Have you already removed and reinstalled CLC,CC,SC and Walrus or is this output from your old installation?

These files are missing.......

```

/var/log/eucalyptus/axis2c.log
/var/log/eucalyptus/cc.log
/var/log/eucalyptus/cc.log.0
/var/log/eucalyptus/cc.log.1
/var/log/eucalyptus/cc.log.2
/var/log/eucalyptus/cc.log.3
/var/log/eucalyptus/cc.log.4
/var/log/eucalyptus/cloud-debug.log
/var/log/eucalyptus/cloud-error.log
/var/log/eucalyptus/cloud-exhaust.log
/var/log/eucalyptus/cloud-output.log
/var/log/eucalyptus/httpd-cc_error_log
/var/log/eucalyptus/jetty-request-******log
/var/log/eucalyptus/jetty-request-******.log
/var/log/eucalyptus/registration.log
/var/log/eucalyptus/sc-stats.log
/var/log/eucalyptus/walrus-stats.log


```

not yet, i install the cloud using Ubuntu Enterprise Cloud (UEC)
and i havent removed or installed CC,CLC,walrus and SC
for sure .. tommorow i'll check it out again

---

