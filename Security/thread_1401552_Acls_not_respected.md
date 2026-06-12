---
title: "Acls not respected"
date: 2010-02-08
forum: Security
---

### Post by hct on 2010-02-08
Hello,
I've set up an ftp server (proftpd) on Kubuntu 9.10. Nothing critical, access is anonymous. Proftpd is set to default to a directory called pub/in. The permission for the pub directory are set to 770 and the owner and group are "administrator". The problem is that when I try to log via ftp I get an "530-Unable to set anonymous privileges." unless I give permissions to others (777). Fair enough, ftp user is in "others" so it makes sense. Enter ACLs. I've run the command:

sudo setfacl  -R -m u:ftp:rwx pub

and now the permissions are:

# file: pub
USER   administrator  rwx     
user ftp        rwx     
GROUP  administrator  rwx     
mask                  rwx     
other                 ---     

# file: pub/in
USER   administrator  rwx     
user ftp        rwx     
GROUP  administrator  rwx     
mask                  rwx     
other                 ---   

but proftp still complains. Tests made from the shell proved the permissions to be correct (or at least they seem correct to me). If they are, how comes that proftpd ignores them? I've seen that a module exists (mod_facl, could not find it in the repositories though) for proftpd that makes it handle acls but why is it required? Now, I know that I can solve my problem by tinkering with the classic permissions (that's what I did in the end) but this makes me wonder what's the use of acls if one has to chase all installed programs one by one to configure them accordingly (where this configuration is possible in the first place) otherwise they will cheerfully ignore the advanced permissions. I've googled around but I didn't find anything that put my doubts to rest. I'm pretty new to this and I'm somewhat confused. What's your experience?

Thanks in advance
hct

---

