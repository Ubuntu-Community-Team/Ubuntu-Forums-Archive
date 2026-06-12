---
title: "different java package installed"
date: 2013-01-15
forum: Server Platforms
---

### Post by associates on 2013-01-15
Hi,

I was having troubled connecting to oracle-java from my Ubuntu Server 12.04 LTS 32bit.

So I went to uninstall it thinking that I can re-install it back into my system by following this steps that I found somewhere in this forum.
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

However, when i was trying to execute the command "sudo apt-get purge oracle-java7-installer*", I was told that it's going to install other version of Java alongside with removing the oracle-java7-installer. Well, there is only two options: Yes (Go ahead) or No (cancel). So I typed in "Y" to go ahead.

It installed all the necessary of Java packages and of course removing the package of oracle-java7-installer.

when it's all done, I did "java -version" and received the following:

java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.5) (6b24-1.11.5-0ubuntu1~12.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

I was wondering if this is all right to have because it's kinda new Java to me. I've been using the oracle-java7-installer for a while already. I prefer to go back to use oracle-java7-installer but am not 100% sure how to go about it as I'm still new to Linux.

By the way, I kept on moving to the next steps where I need to execute the command "sudo add-apt-repository ppa:webupd8team/java"
add-apt-repository ppa:webupd8team/java
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

I'm nervous now as I'm afraid I have mucked up my system.

Any help would be very much appreciated.

Thank you

---

