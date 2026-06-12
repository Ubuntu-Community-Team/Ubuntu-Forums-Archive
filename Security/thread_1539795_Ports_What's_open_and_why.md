---
title: "Ports: What's open and why?"
date: 2010-07-27
forum: Security
---

### Post by ShinHadoken on 2010-07-27
Alright, so I'm locking down my laptop. I know I can use a firewall to ensure nothing gets through that I didn't catch, and I certainly plan on using one, but in the meantime, I want to know what exactly is running on my system.

nmap localhost returns:

```
james@james-linux:~$ nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-07-26 23:33 CDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 994 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
2049/tcp open  nfs

Nmap done: 1 IP address (1 host up) scanned in 0.18 seconds

```

However, I know that localhost goes back to the loopback interface, 127.0.0.1. So, to see what was really open, I ran nmap 192.168.0.108, which is my laptop's IP at the moment.

```
james@james-linux:~$ nmap 192.168.0.108

Starting Nmap 5.00 ( http://nmap.org ) at 2010-07-26 23:33 CDT
Interesting ports on 192.168.0.108:
Not shown: 996 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs

Nmap done: 1 IP address (1 host up) scanned in 0.14 seconds

```

Now if I understand correctly, I can attribute 139 and 445 to my Samba share. That I'm okay with. What I don't know is 111 and 2049. Does anyone know what these ports are, what's running on them, and how I could turn them off, supposing that they are a security risk?

---

### Post by wojox on 2010-07-27
The Network File System (NFS) was developed to allow machines to mount a disk partition on a remote machine as if it were a local disk.

The rpcbind utility is a server that converts RPC program numbers into universal addresses. It must be running on the host to be able to make RPC calls on a server on that machine.

Are you running wubi?

---

### Post by nmaster on 2010-07-27
well nfs is probably network storage.

according to wikipedia, rpcbind is this:

  rpcbind Handles conversion of [remote procedure calls]("http://en.wikipedia.org/wiki/Remote_procedure_call") (RPC), such as from ypbind.

---

### Post by ShinHadoken on 2010-07-27
No, this is a dedicated partition installation.

And I haven't made any NFS shares, nor am I running any RPC software (that I know of). Is there anyway to find out?

---

### Post by nmaster on 2010-07-27
> **ShinHadoken said:**
> No, this is a dedicated partition installation.

And I haven't made any NFS shares, nor am I running any RPC software (that I know of). Is there anyway to find out?

try looking at ```

aptitude search nfs
aptitude search rpc 
```that'll let you see some of the packages that may be installed. not all of them will be relevant, but look at the description.

---

### Post by ShinHadoken on 2010-07-27
I'm not familiar with Aptitude output, does this mean anything to you?

> james@james-linux:~$ aptitude search nfs
v   knfs                            -                                           
p   libfile-nfslock-perl            - perl module to do NFS (or not) locking    
p   libnfsidmap-dev                 - header files and docs for libnfsidmap     
i A libnfsidmap2                    - An nfs idmapping library                  
p   libyanfs-java                   - Yet Another NFS - a Java NFS library      
v   nfs-client                      -                                           
i A nfs-common                      - NFS support files common to client and ser
i   nfs-kernel-server               - support for NFS kernel server             
v   nfs-server                      -                                           
p   nfs4-acl-tools                  - Commandline and GUI ACL utilities for the 
p   nfswatch                        - Program to monitor NFS traffic for the con
p   p3nfs                           - to mount the file systems on the Psion/Sym
p   unfs3                           - User-space NFSv3 Server                   
p   unionfs-fuse                    - Fuse implementation of unionfs            
james@james-linux:~$ aptitude search rpc
p   cipux-rpc-tools                 - Commandline helper tools for XML-RPC serve
p   cipux-rpcd                      - XML-RPC server for CipUX                  
p   event-rpc-perl                  - dummy package to install libevent-rpc-perl
p   gambas2-gb-xml-rpc              - Gambas RPC component                      
p   installation-guide-powerpc      - Ubuntu installation guide                 
p   libcipux-rpc-perl               - XML-RPC routines for perl-based CipUX XML-
p   libdcerpc-dev                   - DCE/RPC library                           
p   libdcerpc0                      - DCE/RPC client library                    
p   libevent-rpc-perl               - Event based transparent Client/Server RPC 
p   libfrontier-rpc-perl            - Perl module to implement RPC calls using X
p   libgssrpc4                      - MIT Kerberos runtime libraries - GSS enabl
p   libjavascript-rpc-perl          - Perl module to process Remote procedure ca
p   libjson-rpc-perl                - Perl implementation of JSON-RPC 1.1 protoc
p   liblua5.1-xmlrpc-dev            - Documentation files for the xmlrpc library
p   liblua5.1-xmlrpc0               - xmlrpc library for the Lua language versio
p   libplrpc-perl                   - Perl extensions for writing PlRPC servers 
p   libprpc-perl                    - Perl extensions for writing pRPC servers a
v   librpc-ocaml-dev                -                                           
i   librpc-xml-perl                 - Perl module implementation of XML-RPC     
p   librpc2-5                       - Remote Procedure Call implementation 2    
p   librpc2-dev                     - Remote Procedure Call implementation 2 (de
p   librpcsecgss-dev                - header files and docs for librpcsecgss    
i A librpcsecgss3                   - allows secure rpc communication using the 
p   libtirpc-dev                    - transport-independent RPC library - develo
p   libtirpc1                       - transport-independent RPC library         
p   libxmlrpc-c3                    - A lightweight RPC library based on XML and
p   libxmlrpc-c3-dev                - A lightweight RPC library based on XML and
p   libxmlrpc-core-c3               - A lightweight RPC library based on XML and
p   libxmlrpc-core-c3-dev           - A lightweight RPC library based on XML and
p   libxmlrpc-epi-dev               - Development files for libxmlrpc-epi0, a XM
p   libxmlrpc-epi0                  - A XML-RPC request serialisation/deserialis
p   libxmlrpc-epi0-dbg              - Debug symbols for libxmlrpc-epi0, a XML-RP
p   libxmlrpc-light-ocaml-dev       - XmlRpc-Light is an XmlRpc library written 
v   libxmlrpc-light-ocaml-dev-nys44 -                                           
p   libxmlrpc-ruby                  - transitional dummy package                
v   libxmlrpc-ruby1.8               -                                           
p   libxmlrpc3-client-java          - XML-RPC implementation in Java (client sid
p   libxmlrpc3-client-java-gcj      - XML-RPC implementation in Java (client sid
p   libxmlrpc3-common-java          - XML-RPC implementation in Java            
p   libxmlrpc3-common-java-gcj      - XML-RPC implementation in Java - gcj nativ
p   libxmlrpc3-java-doc             - XML-RPC implementation in Java (API docume
p   libxmlrpc3-server-java          - XML-RPC implementation in Java (server sid
p   libxmlrpc3-server-java-gcj      - XML-RPC implementation in Java (server sid
p   likewise-open5-rpc              - transitional dummy package                
v   not+powerpc                     -                                           
v   not+powerpc64                   -                                           
p   openser-xmlrpc-module           - XML-RPC support for OpenSER's Management I
p   pearpc                          - PowerPC architecture emulator             
p   php5-xmlrpc                     - XML-RPC module for php5                   
p   python-transmissionrpc          - Transmission RPC client module for Python 
p   rpc2-dbg                        - Remote Procedure Call implementation 2 (de
p   rpc2-tools                      - Remote Procedure Call implementation 2 (ut
p   rpcbind                         - converts RPC program numbers into universa
p   trac-xmlrpc                     - XML-RPC interface to the Trac wiki and iss
p   xml-rpc-api2cpp                 - Generate C++ wrapper classes for XML-RPC s
p   xml-rpc-api2txt                 - Dump an XML-RPC API as a text file 

---

### Post by wojox on 2010-07-27
Look at 

```
man nfs
```

```
man rpc
```

---

### Post by cdenley on 2010-07-27
You can easily find out what processes are listening on what ports. No need to bother with a port scanner, which can be very misleading when scanning a system from itself, even if you scan the external interface.
```

sudo netstat -tulnp

```

---

### Post by nmaster on 2010-07-27
> **ShinHadoken said:**
> I'm not familiar with Aptitude output, does this mean anything to you?

anything with an "i" next to it means that the package is installed.  this means that you do in fact have packages installed that you were unaware of.  try the suggestions from the other posters.

---

### Post by ShinHadoken on 2010-07-30
Alright, I've found that the NFS port is opened by (surprise) nfsd. Does anyone know how I can turn it off? I have no NFS shares to my knowledge. 

The RPC port I'm guessing belongs to either rpc.mountd, rpc.statd, or rpciod, all of which are running, and none of which I can kill. They just keep springing back up. From reading the man pages on these processes, they seem to be linked to NFS. So, once again, anyone have a clue on how to stop NFS and its cronies?

Also, I'm having a Samba issue. I use Gufw as my firewall. I went into Gufw and allowed the ports for Samba. When I go to browse shares on my network, I can't see them, even with these ports open. However, when I turn the firewall off, all is well. I've tried allowing every Samba, SMB/CIFS, and Netbios port I can find, and nothing works. Samba is obviously using a port I don't know about. Any ideas?

---

### Post by cdenley on 2010-07-30
To uninstall your NFS server:
```

sudo apt-get remove nfs-kernel-server

```

---

### Post by ShinHadoken on 2010-08-01
> **cdenley said:**
> To uninstall your NFS server:
```

sudo apt-get remove nfs-kernel-server

```
Hmm, well, good news and bad news. That closed the NFS port. However, Samba appears to be gone (at least, from a port scan. I can't look from another PC because my wireless router is currently down. I plan on ordering a new one Monday) Also, port 111 is STILL OPEN. Any thoughts?

---

### Post by cariboo on 2010-08-01
You probably have to kill portmap,

```
sudo service portmap stop
```

then remove it:

```
sudo apt-get purge portmap
```

when removing packages, it is better to use the purge option, that all the configuration files are removed too.

---

### Post by ShinHadoken on 2010-08-01
> **cariboo907 said:**
> You probably have to kill portmap,

```
sudo service portmap stop
```

then remove it:

```
sudo apt-get purge portmap
```

when removing packages, it is better to use the purge option, that all the configuration files are removed too.
Thank you! Getting rid of portmap closed port 111!

Also, I have some more insight on the Samba issue. When I turn ufw on with all appropriate Samba ports allowed in, and I try to connect to a Samba share on Ubuntu from another PC, root gets emails like this:

> The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 2470 ().

This means there was a problem with the program, such as a segfault.
However, the executable could not be found for process 2470 {changes from email to email, of course).
It may have died unexpectedly, or you may not have permission to debug
the process.

What exactly does this mean for me?

---

### Post by ShinHadoken on 2010-08-01
Did more searching, and any possible port that I uncovered I have already found and tried, and I tried them again just to be certain. Nada. Has anyone else experienced this?

---

### Post by ShinHadoken on 2010-08-02
Bump please

---

### Post by cariboo on 2010-08-03
What is it that you are trying to do? Connect to shares on a windows system, or allow a Windows system to connect to your shares on an Ubuntu computer?

---

### Post by bodhi.zazen on 2010-08-03
> **ShinHadoken said:**
> Bump please

Bump what ?

I do not understand your question either. I also suggest you start a new thread if you have a question unrelated to the default open ports. I also suggest you post in either ABT or General help.

I doubt you will find much assistance for "Bump please" in the security section on a thread that has already been answered.

---

