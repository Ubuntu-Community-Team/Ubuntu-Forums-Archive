---
title: "Update security only?"
date: 2021-02-23
forum: Server Platforms
---

### Post by raskallen on 2021-02-23
Hi

I have fiddled with linux since 1993, but have never had linux as my primary job. I have managed a few servers (10-15 servers) in a couple of my previous jobs. I have patched each of these servers manually. In november '20 I started a new job as a linux admin with responsibility for 300+ virtual linux servers. I have set up Ansible/AWX and written playbooks that works great for patching, deployment and other day to day tasks. I have scheduled monthly patching of all systems and it works quite well. On patch tuesdays I just lean back and wait for patching to finish. I have patched everything on all of the servers.

Recently I got responsibility for for an additional 100+ servers and the owners of those systems wants to apply security patches only. I have googled and asked a question on linuxquestions.org and it seems there's no reason to not grant their wish to only apply security updates. 

However, in my earlier jobs, I have "inherited" (RedHat/CentOS) systems that have never been patched and they have broken badly when I have tried to patch them due to broken dependencies and bad (no) management from the previos sysadmins. Luckily they were virtual servers, so I was able to revert to snapshots. Today my servers are about 30% CentOS/RedHat and the rest on Ubuntu LTS and we are in the process on migrating everything to Ubuntu LTS.

So to my question: If I in the lifetime of servers, which might be up to 5 years (LTS), I need to apply all updates on servers that has only gotten security patches, is there a risk of getting into dependency hell? Or any risk of other breakage? 

My gut says that we should full patch systems regularly to prevent broken dependencies and other potential problems. Is my gut wrong?

---

### Post by ameinild on 2021-02-23
The whole point of running Ubuntu LTS releases should be to avoid dependency hell. As long as you stick to official packages, you should be fine, and you could configure unattended-upgrades to do automatic patching.

But it's always possible to screw up a system with odd third-party repos etc.

However, what you do for your client, there is no right or wrong. But you should agree on what to do, and the client should be aware of any pros and cons of only applying security patches.

---

### Post by LHammonds on 2021-02-23
Yes, the whole point of running LTS is that is that you are not updating to the latest-bleeding-edge application versions in the standard repositories.  Apache and PHP for example do not jump major versions during the life of the LTS.  To my recollection, I have not had any standard services break due to an LTS upgrade.

The main times that require careful testing are going to different LTS version which means newer baseline package such as Apache and PHP...which I would recommend installing a new server and installing the new baseline packages and trying to get the configuration working like your old server and backup/restore the data to see if it works...then perform an actual migration after confirming a good-working upgrade path/procedure.

And congrats on the job.  I've been responsible for about 200 servers in a mixed environment and I sure do prefer Linux servers over all other kinds.  Unfortunately, jobs tend to drive what application systems are used which in turn drive which operating systems are used.  Very difficult to not run a mixed environment.

LHammonds

---

