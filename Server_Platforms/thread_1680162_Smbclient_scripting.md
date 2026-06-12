---
title: "Smbclient scripting"
date: 2011-02-02
forum: Server Platforms
---

### Post by Sorensiim on 2011-02-02
This lovely little headache has landed on my desk and I'm pretty much stuck right now, so any and all pointers are appreciated :)

We have a bunch of Ubuntu servers running the backend for the POS (Point-Of-Sales, not the other meaning of POS ;)) software. The software is still under development so a bunch of features are missing. Until they get fixed, we have to make our own work-arounds - this is one of them.

On the server, in a path like ```
/usr/local/username/instances/[Variable 1]/bo/komm/in/uploadFile/[Variable2]/
```
are the files we need copied to a windows server. Mounting the windows share would be the easiest solution, but we don't have root access to the servers, so we'll need to use smbclient in stead.

"Variable1" can be any one of 30-40 different folders, one for each store. Under each of the "Variable1" folders, there is the path to "Variable2" as mentioned above. "Variable2" is 2-4 different folders, in which the files we need are found. The files are named after the time they were first generated, so I'll need the script to create a subfolder on the server named after "Variable1" and then a subfolder for each "Variable2" folder, to keep the files organised.

I do a bit of scripting here at work, but mostly vbscript (sorry!) on our windows platform. I made the mistake of mentioning that I've been running Ubuntu as my main OS at home since 2006, so now this task has landed on my desk - This is all I have so far:

```
cd /usr/local/gkretail/instances
for dir in $(find . -maxdepth 1 -iwholename '*/BO-*' -type d); do
	smbclient '//prague-1/IT/GK_Printer_Journals' -U username%Password -W DOMAIN -c mkdir $dir
done	
```
All I get is this:
```
Domain=[DOMAIN] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]
mkdir <dirname>

```
I guess the variable isn't passed properly to smbclient, right?

---

### Post by SeijiSensei on 2011-02-02
> Mounting the windows share would be the easiest solution, but we don't have root access to the servers, so we'll need to use smbclient in stead.

Take a look at smbmount as an alternative.  You can mount remote SMB file shares into the directory tree just as you would with something like NFS.  You'd use it like this:

smbmount //server/share /mnt/point [-o options]

I usually put the username and password into a file that only root can read and use the "credentials" option to authenticate.

See "man smbmount" for more details.  smbmount is in the "smbfs" package.

---

### Post by koenn on 2011-02-02
> **Sorensiim said:**
> T
I guess the variable isn't passed properly to smbclient, right?

sort of.
your smbclient statement is not wellformed.

according to the smbclient man page, you need something like

```

smbclient -W DOMAIN -U username -c "mkdir $dir"  //server/share userpassword

```
note the order of arguments, and especially the quotes around the -c option value - you definitely need those to pass that command correctly to the samba server.

also, you may need an option -D directory for subdirs of //server/share; I'm not quite sure smbclient will accept //server/share/subdir as "service"

Also, check that your find command generates the expected values and that they are correct for the paths you want to create on the samba server.



All in all, you're probably better of doing what SeijiSensei suggests : mount those shares on a linux machine and and use standard linux commands to create your tree

---

