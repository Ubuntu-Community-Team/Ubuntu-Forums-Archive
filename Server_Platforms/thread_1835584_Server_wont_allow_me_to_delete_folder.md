---
title: "Server wont allow me to delete folder"
date: 2011-08-29
forum: Server Platforms
---

### Post by ameharhughes on 2011-08-29
Hi All...


I have VPS with Ubuntu 8.04 installed. It is a web server.

I am having trouble deleted two folder with SSH, the commans seem to run ok, they dont give any errors but the folders remain.

I have ran "rmdir --ignore-on-non-empty tmp" and I have ran rm -rf tmp

I have also ran chmod 777 tmp as well and so I am a stuck. Also ran ls -l and permissions have taken place.

thanks in advance.

---

### Post by arrrghhh on 2011-08-29
I don't think you can rm /tmp - why are you trying to remove that directory...?

You should be able to remove stuff within /tmp, but again I don't think you can remove the entire directory itself.

---

### Post by ameharhughes on 2011-08-29
Sorry, should said before, its not the servers tmp folder, it was a web installation.

it var/www/vhosts/purplecamel.co.uk/subdomains/clients/balbir/httpdocs

and in this folder there is /tmp and /blogs and these are the folders that wont delete

---

### Post by arrrghhh on 2011-08-29
> **ameharhughes said:**
> Sorry, should said before, its not the servers tmp folder, it was a web installation.

it var/www/vhosts/purplecamel.co.uk/subdomains/clients/balbir/httpdocs

and in this folder there is /tmp and /blogs and these are the folders that wont delete

You've tried to preface the rm command with 'sudo'?

You've chmodded, have you chown'd?  Although with 777 I don't think owner will matter...

---

### Post by hyper2hottie on 2011-08-29
Try stopping the web server.  I've had similar troubles with IIS in windows.

---

### Post by arrrghhh on 2011-08-29
> **hyper2hottie said:**
> Try stopping the web server.  I've had similar troubles with IIS in windows.

D'oh, I didn't even think about a process holding a lock on the file.

Verify if any processes have a lock with lsof.

---

