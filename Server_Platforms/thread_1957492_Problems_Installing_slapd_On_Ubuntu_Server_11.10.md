---
title: "Problems Installing slapd On Ubuntu Server 11.10"
date: 2012-04-12
forum: Server Platforms
---

### Post by 1n73rn37_j3d1 on 2012-04-12
I'm in the process of installing Oracle Database 11g R2 on an Ubuntu 11.10 server here at work. I'm following [_this_]("https://forums.oracle.com/forums/thread.jspa?messageID=9596361") guide from the Oracle support forums. I'm currently in the process of installing all of the dependency packages, one of which is **slapd**.

When I go to install slapd, I get this error:
> (Reading database ... 64726 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.25-1.1ubuntu4.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Setting up slapd (2.4.25-1.1ubuntu4.1) ...
Usage: slappasswd [options]
  -c format     crypt(3) salt format
  -g            generate random password
  -h hash       password scheme
  -n            omit trailing newline
  -s secret     new password
  -u            generate RFC2307 values (default)
  -v            increase verbosity
  -T file       read file for new password
  Creating initial configuration... Loading the initial configuration from the ldif file () failed with
the following error while running slapadd:
    str2entry: invalid value for attributeType olcRootPW #0 (syntax 1.3.6.1.4.1.1466.115.121.1.15)
    slapadd: could not parse entry (line=1051)
dpkg: error processing slapd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've been searching around the Web for an answer to these errors, but I just can't seem to find any. Can anyone help? If I'm leaving out any key information, or you'd like to know more about the system I'm running just in case something's getting in the way, I'll be more than happy to supply that information.

Thanks in advance!

---

