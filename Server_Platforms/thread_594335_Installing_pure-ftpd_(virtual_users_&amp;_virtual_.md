---
title: "Installing pure-ftpd (virtual users &amp; virtual quotas) and need help"
date: 2007-10-27
forum: Server Platforms
---

### Post by kentl on 2007-10-27
Hi!

I'm setting up pure-ftpd, and I'm having some problems. What I have done is, first installing it and creating some accounts using the command line:

```
# Installation and configuration of Pure-FTPd [4]
   1. "sudo aptitude install pure-ftpd"
   2. "sudo groupadd ftpgroup"
   3. "sudo useradd -g ftpgroup -d /dev/null -s /etc ftpuser"
   4. "sudo mkdir /home/ftpusers/thefirstuser"
   5. "sudo mkdir /home/ftpusers/seconduser"
   6. "sudo mkdir /home/ftpusers/lastuser"
   7. "sudo pure-pw useradd thefirstuser -u ftpuser -g ftpgroup -d /home/ftpusers/thefirstuser -N 300000"
   8. "sudo pure-pw useradd seconduser -u ftpuser -g ftpgroup -d /home/ftpusers/seconduser -N 4096"
   9. "sudo pure-pw useradd lastuser -u ftpuser -g ftpgroup -d /home/ftpusers/lastuser -N 4096"
  10. "sudo pure-pw mkdb"
  11. "sudo pure-pw list" prints:
      thefirstuser         /home/ftpusers/thefirstuser/./
      lastuser       /home/ftpusers/lastuser/./
      seconduser      /home/ftpusers/seconduser/./
  12. "chown -c -R ftpuser:ftpgroup ftpusers/" prints:
      changed ownership of `ftpusers/thefirstuser' to ftpuser:ftpgroup
      changed ownership of `ftpusers/seconduser' to ftpuser:ftpgroup
      changed ownership of `ftpusers/lastuser' to ftpuser:ftpgroup
      changed ownership of `ftpusers/' to ftpuser:ftpgroup
```

After that I consulted [http://download.pureftpd.org/pub/pure-ftpd/doc/README](http://download.pureftpd.org/pub/pure-ftpd/doc/README) and [http://www.penguin-soft.com/penguin/man/8/pure-ftpd-wrapper.html](http://www.penguin-soft.com/penguin/man/8/pure-ftpd-wrapper.html) ,trying to puzzle things together.

I did some more configuring by creating the files I thought were necessary but not yet there. In total (default + my creations) I got these files with contents: (on the form 'file => contents' using that for... do bash line)

```
cd /etc/pure-ftpd/auth/
for i in `ls` ; do echo -n $i && echo -n " ==> " && cat $i ; done
65unix ==> no
70pam ==> yes
cd ../conf/
AltLog ==> clf:/var/log/pure-ftpd/transfer.log
IPV4Only ==> yes
MinUID ==> 1000
NoAnonymous ==> yes
PAMAuthentication ==> yes
PureDB ==> /etc/pure-ftpd/pureftpd.pdb
UnixAuthentication ==> no

```

[LIST=1]
[*]How do I know which file I need to create for the Wrapper that will match an option in the README? The wrapper man page doesn't say anything about what each file actually does, only their names.
[*] At the moment I'm able to login using normal accounts. I only want to be able to login using virtual accounts. How do I do it? (As you can se above, I do have a UnixAuthentication file with the contents "no" in it.)
[*] At the same time. I am NOT able to login using virtual accounts. :confused:
[/LIST]

Thanks for your time! Any help would be greatly appreciated, except suggestions to use something else or questions about why I want it to work with virtual users only. I have my reasons. :)

---

### Post by kentl on 2007-10-28
I solved it. The configuration above works if you replace the last CODE box with this one (the first one is all right and need not be changed!):

```

> cd /etc/pure-ftpd/auth
> ls -ls
0 lrwxrwxrwx 1 root root 26 2007-10-29 02:21 50pure -> /etc/pure-ftpd/conf/PureDB
0 lrwxrwxrwx 1 root root 26 2007-10-10 02:39 65unix -> ../conf/UnixAuthentication
0 lrwxrwxrwx 1 root root 25 2007-10-10 02:39 70pam -> ../conf/PAMAuthentication
> # The above indicates that the three files are symlinks. The PureDB one is needed for the virtual users.
> cd ../conf/
> for i in `ls` ; do echo -n $i && echo -n " ==> " && cat $i ; done
AltLog ==> clf:/var/log/pure-ftpd/transfer.log
IPV4Only ==> yes
MinUID ==> 1000
NoAnonymous ==> no
PAMAuthentication ==> no
PureDB ==> /etc/pure-ftpd/pureftpd.pdb
UnixAuthentication ==> no

```

In the box above UnixAuthentication ==> no means that you need to create a file called UnixAuthentication with the content no.

This will end up in this start line (which the wrapper outputs after interpreting the files used to configure proftpd using it)
```
/usr/sbin/pure-ftpd -l puredb:/etc/pure-ftpd/pureftpd.pdb -O clf:/var/log/pure-ftpd/transfer.log -4 -u 1000 -B
```

---

