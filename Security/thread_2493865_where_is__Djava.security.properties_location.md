---
title: "where is  Djava.security.properties location?"
date: 2023-12-27
forum: Security
---

### Post by mehdi3524 on 2023-12-27
Hi ,
/etc/java/security is empty
 but it works when i run 
openssl s_server -accept 4443 -cert localhost.pem -key localhost.key | grep ^CIPHER
keytool -J-Djava.security.properties=file://$HOME/java.security -printcert -sslserver localhost:4443 > /dev/null;echo $?

but i can't find java.security.properties location?
i use 
OpenJDK Runtime Environment Temurin-17.0.8.1+1 (build 17.0.8.1+1)
and Ubuntu 20.04.
Best regards

---

### Post by #&amp;thj^% on 2023-12-27
Have you looked in
```
/etc/java-17-openjdk/security/
```
ie:
```
ls /etc/java-17-openjdk/security/
blocked.certs   java.policy    nss.cfg  public_suffix_list.dat
default.policy  java.security  policy

```
And on my system Debian 12 xfce4
```
cd  /etc/java-17-openjdk/
### and
jconsole

```

---

### Post by mehdi3524 on 2023-12-28
hi.
thanks i find the files name  you add ,  in /usr/lib/jvm/java-17-openjdk-amd64/conf/security/java.security , i think because i use different jdk 
thanks for your help
Best  regards

---

### Post by #&amp;thj^% on 2023-12-28
I find them both the same:
```
[COLOR="#FF0000"]]&#9472;[/etc/java-17-openjdk/security][/COLOR]
&#9492;&#9472;&#9472;&#9596; $tac java.security |grep Djava
# or overridden on the command line via -Djava.security.properties
# or -Djava.security.auth.login.config=somefile. If commented out or set to
# allowed to be passed on the command line with -Djava.security.policy=somefile
#   % java -Djava.security.egd=file:/dev/random MainClass
# -Djava.security.debug=jca property to debug these errors.
#    -Djava.security.properties==<URL> (2 equals),
#    -Djava.security.properties=<URL>

```
And
```
[COLOR="#FF0000"]]tac  /usr/lib/jvm/java-17-openjdk-amd64/conf/security/java.security |grep  Djava[/COLOR]
# or overridden on the command line via -Djava.security.properties
# or -Djava.security.auth.login.config=somefile. If commented out or set to
# allowed to be passed on the command line with -Djava.security.policy=somefile
#   % java -Djava.security.egd=file:/dev/random MainClass
# -Djava.security.debug=jca property to debug these errors.
#    -Djava.security.properties==<URL> (2 equals),
#    -Djava.security.properties=<URL>

```
Both returns are *cut short* due to length, but both are identical in syntax

---

