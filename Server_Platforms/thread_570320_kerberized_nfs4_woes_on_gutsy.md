---
title: "kerberized nfs4 woes on gutsy"
date: 2007-10-08
forum: Server Platforms
---

### Post by garba on 2007-10-08
hi all, i've just installed gutsy and found out that i am no longer able to mount my kerberized nfs4 shares served by my debian etch server... it worked great on feisty but now on gutsy i get the following when issuing a mount:

rpc.gssd[6663]: WARNING: Failed to create krb5 context for user with uid 0 with any credentials cache for server

and the mounting miserably fails with a permission denied... :(

any help would be greatly appreciated

---

### Post by djsaltarelli on 2007-10-08
I'm not too familiar with kerberized services on unix, but does the new install have all the same kerberos credentials as the previous install?  It's possible that the computer has to have a trusted account in addition to any user account that might be involved.

The message reference to 'uid 0' makes me thing you're doing the mount as root and maybe that's not allowed by some config setting. Also, the credentials cache reference makes me thing it's looking only in a cache and it doesn't have any valid cached credentials available, so it denies you. Maybe you can flush that cache on either or both of the client/server sides to generate new credentials that will work.

I would also look at the kerberos config files from the backup of the old install versus the new one and look at any changes that have occurred in the default config files for the two different versions of kerberos (old/feisty and new/gutsy) and nfs4.

Also, maybe you can turn up the logging level on the server and get more details that way.

/dj

---

### Post by garba on 2007-10-11
thanks for your help, but it looks like the new nfs version that comes with gutsy breaks compatibility with my debian nfs4 server...
yeah i'm using the same krb keytabs as the previous install to make my client host trusted, anyway it doesn't matter who issues the mount commant since mount is setuid 0

what bugs me the most is the following:

[email]root@ws-05:/home/a.garb[/email]arini# klist -c /tmp/krb5cc_machine_CORSAROCONSULTING.COM
Ticket cache: FILE:/tmp/krb5cc_machine_CORSAROCONSULTING.COM
Default principal: nfs/ws-05.corsaroconsulting.com@CORSAROCONSULTING.COM

Valid starting     Expires            Service principal
10/11/07 22:13:09  10/12/07 08:13:09  krbtgt/CORSAROCONSULTING.COM@CORSAROCONSULTING.COM
        renew until 10/12/07 22:13:09
10/11/07 22:13:10  10/12/07 08:13:09  nfs/svc.corsaroconsulting.com@
        renew until 10/12/07 22:13:09

the krb realm is missing from the last entry (svc is our nfs4 server)

if we can't get nfs4 to work we'll have to stick with feisty, too bad cause we'll be redeploying all our clients soon and the new kubuntu gutsy looks amazing

---

### Post by jbardin on 2007-10-12
I have both kerberized nfs3 and nfs4 available, and neither works.
Someone else has reported this too: [https://bugs.launchpad.net/bugs/148600](https://bugs.launchpad.net/bugs/148600)

This is a big deal-breaker for me as well. I tried to pull the packages from upstream, but the dependencies are laid out differently.

-jim

---

### Post by sappomanno on 2007-10-19
Hullo,

here at unibz.it NFSv4 work for me. I Just have upgraded a client from feisty to gutsy and it seems to be ok. Our server is a Ubuntu 6.10

I have only some problems by renewing the machine credentials automatically but i should have fixed it with a cron tab

Ciao

Cristiano

---

### Post by garba on 2007-10-19
hello sappomanno, i'm glad it works for you, just curious about this: is file locking properly woking for you? does the server properly prevents a file from being accessed when it's already been opened for write/read operations by another client? this is the only one feature that got me sold on nfs instead of relying on other solutions such as sshfs, which is great but not very suitable for shared folders

---

### Post by sappomanno on 2007-10-19
I use nfsv4 in our lab setup for sharing homes. I did run some test for  file locking but only on a single client.
If you can provide me with a distributed test suite I would be glad to run it for you.

Ciao

Cristiano

---

### Post by kwcoffman on 2007-10-19
Hello,
I discovered this forum via a reference in the nfs mailing list.  Could you tell me what versions of nfs-utils and kerberos are used in gutsy?

The other bug reference in this thread pointed to a kernel problem.  I assume that is not the same as you are seeing?  In any case, what kernel version is in gutsy?

K.C.

---

### Post by garba on 2007-10-20
thanks everybody for your help

@sappomanno

have no clue if such a suit exists, but it looks like file locking is not working as expected in nfs4, did some "hands on" testing with two feisty clients but it didn't work: the same file could concurrently be opened for read-write operations by both clients at the same time...sic! perhaps it's just my nfs4 which is misconfigured, or perhaps it's just the way it's supposed to work

@kwcoffman

the nfs package that comes with gutsy comes with a git-20070709 tag in its package name, my guess is some major change took place upstream making it not backward compatible with my debian etch nfs4 server, anyway i believe the problem i'm having doesn't seem to be related to the kernel bug mentioned on launchpad, must be due to some kerberos weirdness... this is what i get at mount time

Oct 20 22:16:12 ws-05 rpc.gssd[10530]: handling krb5 upcall
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: Full hostname for 'svc.corsaroconsulting.com' is 'svc.corsaroconsulting.com'
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: Full hostname for 'ws-05.corsaroconsulting.com' is 'ws-05.corsaroconsulting.com'
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: Key table entry not found while getting keytab entry for 'root/ws-05.corsaroconsulting.com@'
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: Success getting keytab entry for 'nfs/ws-05.corsaroconsulting.com@'
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: INFO: Credentials in CC 'FILE:/tmp/krb5cc_machine_CORSAROCONSULTING.COM' are good until 1192946856
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: INFO: Credentials in CC 'FILE:/tmp/krb5cc_machine_CORSAROCONSULTING.COM' are good until 1192946856
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: using FILE:/tmp/krb5cc_machine_CORSAROCONSULTING.COM as credentials cache for machine creds
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: using environment variable to select krb5 ccache FILE:/tmp/krb5cc_machine_CORSAROCONSULTING.COM
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: creating context using fsuid 0 (save_uid 0)
Oct 20 22:16:12 ws-05 rpc.gssd[10530]: creating tcp client for server svc.corsaroconsulting.com
Oct 20 22:16:13 ws-05 rpc.gssd[10530]: creating context with server [email]nfs@svc.corsaroconsulting.com[/email]
Oct 20 22:16:13 ws-05 rpc.gssd[10530]: WARNING: Failed to create krb5 context for user with uid 0 for server svc.corsaroconsulting.com
Oct 20 22:16:13 ws-05 rpc.gssd[10530]: WARNING: Failed to create krb5 context for user with uid 0 with credentials cache FILE:/tmp/krb5cc_machine_CORSAROCONSULTING.COM for server svc.corsaroconsulting.com
Oct 20 22:16:13 ws-05 rpc.gssd[10530]: WARNING: Failed to create krb5 context for user with uid 0 with any credentials cache for server svc.corsaroconsulting.com
Oct 20 22:16:13 ws-05 rpc.gssd[10530]: doing error downcall
Oct 20 22:16:13 ws-05 rpc.gssd[10530]: destroying client clnt3
Oct 20 22:16:13 ws-05 rpc.gssd[10530]: destroying client clnt2

same krb5.conf, same keytab on feisty: it works, albeit with some shortcomings as mentioned above ie no file locking

i'm now looking into samba, although i don't believe it makes much sense in a linux only environment as ours is, anybody knows if i can get kerberos auhentication with samba to work without having to rely on a windows domain controller? besides these two options to serve shares to my lan i don't know what else to turn to, openafs might be another option, but it sounds like plain overkill

thoughts? :)

---

### Post by sappomanno on 2007-10-22
Ciao Garba,

for the locking issue I suggest to join the nfsv4 mailing list at

[http://linux-nfs.org/cgi-bin/mailman/listinfo/nfsv4](http://linux-nfs.org/cgi-bin/mailman/listinfo/nfsv4)

where you can get the help of the maintainers of the nfsv4 implementation for linux.

Anyway gutsy seems to work fine for me now, but as I couldn't identify the problem I will run a small number of clients as test before a site-wide deploy

Bye

C.

---

### Post by kwcoffman on 2007-10-22
I asked about the kerberos version because it may be related to this:

[http://www.webservertalk.com/archive97-2007-4-1880493.html](http://www.webservertalk.com/archive97-2007-4-1880493.html)

So something that works with an older version of Kerberos may not work with a new version of Kerberos (>= 1.6)  if you have an officially misconfigured server principal. (The server principal, and keytab, should have only a des-cbc-crc key).

---

### Post by garba on 2007-10-24
> **kwcoffman said:**
> I asked about the kerberos version because it may be related to this:

[http://www.webservertalk.com/archive97-2007-4-1880493.html](http://www.webservertalk.com/archive97-2007-4-1880493.html)

So something that works with an older version of Kerberos may not work with a new version of Kerberos (>= 1.6)  if you have an officially misconfigured server principal. (The server principal, and keytab, should have only a des-cbc-crc key).

thanks a lot kwcoffman, as soon as i have some spare time i'll give it a shot and let you guys know * crosses fingers *

---

### Post by garba on 2007-10-24
kwcoffman YOU ARE DA MAN!!!!

all i had to do was recreating both the server and the clients' keytabs with ktadd -e des in the kerberos admin console and bang that was it! it works now! thanks a lot!

---

