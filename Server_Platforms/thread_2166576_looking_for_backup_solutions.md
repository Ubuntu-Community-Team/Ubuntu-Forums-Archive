---
title: "looking for backup solutions"
date: 2013-08-10
forum: Server Platforms
---

### Post by chadk5utc on 2013-08-10
I have not attempted a project on this scale until now. I have a number of clients/locations each has two linux computers.
Client A has 4 locations Mom and Pop stores
Client B has 200 locations
Client C has 200 locations     These numbers are just examples but you get the idea.
Client D has 300 locations
Each of them is responsible to local backups(yea right) of all machines(local) to be stored externally. In reality I've had 3 locations suffer HDD failures in the last week, loosing irreplaceable financial data.
Goal provided/offered as secure offsite backup. I personally have started doing manual backups of config files only on one machine totaling 1.2mb and one directory on the other machine totaling 125mb then pulling these files to my external drive. This is just not practical or efficient. So my question now is what is the "best" method and suggestions. I have a storage server with more than enough room running linux now.
1. How often would you do full backup, weekly,bi-weekly, monthly? backups done incrementally after full backups.
2. How would you send these backups to remote server? scripts, rsync, other?
3.  what suggestions do you have for timing these transfers so that I do not cause a bandwidth/bottleneck within my own network-backup server?

Thanks
 Chad

---

### Post by tripp98 on 2013-08-14
Due to the large number of clients you will have to have the clients push data to you.  Have all the data placed in one location at each customer.  Then securely push the data to you.  via sftp or private vpn etc.  

Another option is to have each client backup to the cloud.  Ubuntu One has 5gb of storage and each customer could back their data up directly there.

please update and let everyone know what you ended up doing.

---

### Post by SeijiSensei on 2013-08-15
Are all the client machines storing "irreplaceable" data on their own drives?  Do you not use centralized file/database servers at each location?  I cannot fathom how you would manage networks with this many clients where storage is not centrally maintained.  If they write data to MySQL/PostgreSQL use one or two servers and connect to them over the network.  If they write data to local files, mount a share on each machine with NFS at boot and write the data to it.  Then you are left with the task of backing up a few servers, not hundreds of workstations.

---

### Post by TheFu on 2013-08-16
I'd like to reply, but know that there is too much unknown information to provide a good solution. Available network bandwidth will matter a bunch in the final solution and don't discount using FedEx to ship HDDs around, if that is really needed.

The types of clients and servers at each location would matter a bunch too.

Since it is financial data, encryption **must** be part of the solution - actually, they should be encrypting data on their local servers AND local desktops too.

Rolling your own solution will likely have issues during recovery, which will make recovery much longer  than expected, if it is even possible.  You'll want to consult with a backup and disaster recovery architect before going too far.  PM me if you'd like more information.

---

### Post by chadk5utc on 2013-08-17
Hello all Ive been quite busy sorry for the delay and missing info. Clients are "supposed" to be backing up their own info and responsible for this plane and simple however in reality they have to date Failed. I am attempting this on my own to provide some disaster recovery and to simplify my own job as much as possible.
1. All network traffic is VPN and Encrypted
2. Network access is restricted to less than 10 people Nation wide. Our IT only.
3. Yes clients are storing their own data locally, and are supposed to be backing it up and storing backups centrally offsite.
4. The largest single problem is Client IT replacing hardware (HDD) without properly configuring it to the location, and without their backups recovery is Null at this point. I have(we have) told them repeatedly. This is costing us time, money, resources best used elsewhere to reconfigure these Systems because they failed to do so properly then whine for us to do it.
5. Bandwidth at this point is going to be some what an issue as clients are responsible for this connection to our network. The config files can be backed up and retrieved from all locations nationwide within 30minutes. However the main backups are @125mb each and take about 3+- minutes each, some locations are much faster at less than a minute and some are slower (DSL or rural DSL) for what its worth all are business class connections.
6. I have been testing this theory using my office pc 
7 I agree this will likely have to be pushed from location to our office due to the amount of data and number of locations. This was not something that we set out to do initially but after recent failures we are looking into it and want to keep this in-house.

---

### Post by TheFu on 2013-08-17
With that number of clients, I hope you are using some sort of CM management ... to be able to quickly reset all configs to known-good values.  Something like Salt, Ansible, puppet, Chef, CF-Engine ... something.  Using one of those tools will let you rebuild/reset a server from the ground up with just a few minutes of your time. Then it just becomes a matter of restoring the back up data.  I've only been using Ansible for a few months and have much to learn still, but it is smart about not doing anything that isn't needed - if the settings already exist, they don&#8217;t get redone.  I love the reusable nature of the "tasks", "plays" and "playbooks" with ansible.  So far, I haven't had to write **any** new  modules. The existing library has covered everything needed.  Anyway, one of those tools will make your reinstallation into just a few manual steps, followed by a step-back and wait step as the tool handles the rest.  Rerunning it will re-inforce your desired settings regardless of local changes.
With Ansible, they say you can be up and working in 15 minutes. While true, understanding the best layout for your tasks, plays and playbooks can take a little longer. There is a new Ansible introduction video [http://www.ansibleworks.com/quickstart-video/](http://www.ansibleworks.com/quickstart-video/) just published this month which blows away all the others.  I'm just a happy user, not even a client. ;)  Ansible lets you control the number of parallel servers where tasks run concurrently.  On the client-side, the requirements are minimal. A base Ubuntu Server 10.04 install with ssh-server should already meet the minimums, which is pretty sweet. If you have older python versions, there might be 2 python dependencies to be installed ... or you can do it 100% without any python, it will just be more work for you, since the existing modules are python.

With that number of systems, you may want to jump directly into Salt (Salt-Stack). Salt is supposed to be much, much faster than the other options.

125MB isn't all that much data for backups really. The key is to get it uncorrupted when the systems are not being used. If the data is stored inside a DB, just dump the DB and compress it, then grab that file, not the entire system.   Anyway, I assume you have that down.  I was worried that you had multiple GBs for each system.  I'd calculate a backup window for each location based on local needs and when the upstream bandwidth can be used without impacting daily operations. 

I don't want to talk down to you, so what backup solutions have you already considered?  Backups and DR are my life. ;)

I stopped using old-school backup tools around 2005.  No "full, then 6 days of incremental backups" anymore.  These days, the 1st backup is a full and all the following backups are incremental.  They are stored in a reverse incremental way - the last backup looks like a mirror, with older backups just being the diffs from the prior backup.  That means you cannot "break the chain" in the backups (i.e. delete any intermediate backup), but you can tell the system to delete all backups over 60 days old.  rdiff-backup is the tool I use.  You can push or pull backups with it. It is based on librsync and data goes over an ssh tunnel by default. If you already have a VPN, you can disable the ssh use. Scripting backups doesn't take too much time after the first one is written.  [http://www.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://www.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup) sorta explains. I've implemented this [http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines](http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines) method across about 30 VMs. It has been working for almost 2 years.  I have restored a few VMs with it too.  Ansible was not part of those restores, but I'm planning to add that method too. Anything to reduce my manual effort and have a reproducible solution.  Don't the *cool kids* call that **DevOps** now?

---

### Post by SeijiSensei on 2013-08-17
> **chadk5utc said:**
> Yes clients are storing their own data locally, and are supposed to be backing it up and storing backups centrally offsite.

Let's start with this policy which, I would argue, is a recipe for disaster.  

First, what kinds of data are we talking about here?  Are the clients writing data to SQL databases, or are they writing to files?  Where are these files stored?  No client machine should be writing any permanent data to itself; anything worth saving needs to be written to well-managed file server(s).  As I said above, I would install file/database servers at every physical location to serve the local workstations, then back up the servers overnight to a central location.

---

