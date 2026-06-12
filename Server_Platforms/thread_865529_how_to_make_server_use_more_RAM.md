---
title: "how to make server use more RAM"
date: 2008-07-20
forum: Server Platforms
---

### Post by nephish on 2008-07-20
Hey there all. 

I have a mysql server that we use in our company to both process input data and serve the info on the internet. The database is very very busy. When i watch the system monitor, I don't seem to be using any RAM. I have 8 dual core processors that average about 40 - 70 percent. But i have 16 Gig of RAM that does not seem to be used hardly at all. I thought that it would create a big performance increase if we could utilize a lot more of our resources. 

Any tips would be greatly appreciated.

---

### Post by mbeach on 2008-07-20
very very busy is quite a relative term.  8 cpus averaging 50 percent does seem to suggest a busy server however. 

The problem with throwing more resources at a database server is that you may not get any performance increase.  It depends on the database design and the queries being thrown at it.

I highly recommend anyone dealing with relational databases on a day to day basis read "The Art of SQL"
[http://www.amazon.com/Art-SQL-Stephane-Faroult/dp/0596008945](http://www.amazon.com/Art-SQL-Stephane-Faroult/dp/0596008945)
There's a chapter in there about just what you are observing and the steps you are taking in an attempt to improve performance.

sorry - perhaps not much of an answer.  One thing to make sure is that you have the server version installed - I believe it is more able to handle the large amount of ram than the desktop version which I think is either optimized for or maxed out at 4GB.  I think windependence just posted the specifics on that somewhere today.

---

### Post by tamoneya on 2008-07-20
I dont know much about Mysql and databases but If you want more of your stuff to be loaded into RAM you could try adjusting the swapiness.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by tinny on 2008-07-20
The FIRST place to look is definitely the /etc/mysql/my.cnf file!

You will find several preconfigured example configurations that will give you a good starting point for your tuning.

[http://dev.mysql.com/tech-resources/articles/mysql_intro.html#SECTION0001500000]("http://dev.mysql.com/tech-resources/articles/mysql_intro.html#SECTION0001500000")

[http://dev.mysql.com/doc/refman/5.0/en/option-files.html#option-files-preconfigured](http://dev.mysql.com/doc/refman/5.0/en/option-files.html#option-files-preconfigured)

---

### Post by nephish on 2008-07-20
Thanks, gents, i have already adjusted the swapiness, but just don't know what all the variables in my.cnf mean. 
thanks for the links 
appreciate it. Just did not know where to start.

---

### Post by tinny on 2008-07-20
> **nephish said:**
> Thanks, gents, i have already adjusted the swapiness, but just don't know what all the variables in my.cnf mean. 
thanks for the links 
appreciate it. Just did not know where to start.

"swap" is the enemy of MySQL databases! (And is not going to help you with your problem)

You should just start by renaming "my-large.cnf" to "my.cnf" and restart your MySQL instance.

---

### Post by nephish on 2008-07-20
should i have no swap at all ? 
my-large.cnf is where i started. I have a couple of tables that get written to up to 4 times per second. I really need more optimization in inserts than deletes.

thanks again for your time.

---

### Post by tinny on 2008-07-20
> **nephish said:**
> should i have no swap at all ? 
my-large.cnf is where i started. I have a couple of tables that get written to up to 4 times per second. I really need more optimization in inserts than deletes.

thanks again for your time.

I think usually swap should be x2 physical memory.

Also turn on the Query cache if you haven't already! (Wont help your inserts or deletes)

FYI (swappiness): [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

Same applies for desktops.

Q: Is your hard drive very busy? (you might be using swap too much)

---

### Post by nephish on 2008-07-20
what is a good app to monitor hard drive I/O, we have a RAID 5, with 5 hard drives.

---

### Post by tinny on 2008-07-20
First try a blinking LED. :) (before you get too complicated)

If its going all the time you are swapping too much.

Do you have an entry for "vm.swappiness" in your /etc/sysctl.conf file? If so what is it? (add vm.swappiness at the bottom if you dont have it)

You could first try setting it to "vm.swappiness=5"

You will need to reboot the server (I think)

---

### Post by gtdaqua on 2008-07-21
1. You have 16GB of memory. So try not to use swap. Confidently set the vm.swappiness value to 0.

2. What is the filesystem you are using? Try not Ext3 on your DB environment. For maxing performance, you need a specific performer than an overall performer. Ext3 is rock-solid on all roles but not an optimized one for DBs. Consider JFS or XFS. ReiserFS is good if you are handling files under 4KB. But beware of XFS and ReiserFS - recovering corrupt partitions on these could be a nightmare.

3. Bottomline is, how good is your db architecture? Have you put data and index on different physical drives? This is the strongly recommended model. Debate between MyISAM and Innodb to suit your needs. Try to store temporary values on the memory itself. Split the partions based on the DB roles. For e.g. Some tables require more reads than writes. Put those on a single partition and set "noatime" option (see below).

3a. Once you have decided the filesystem, debate on the switches you should use when mounting the FS. "noatime" is generally conisdered a superb option when mounting FS, because unnecessary writes are not performed. If you have a fantastic power source, consider using "data=writeback" option - you could lose data during power loss.

4. Kernel boot parameters could siginificantly throttle I/O of the server. Debate between parameters "elevator=deadline" and "elevator=noop" - you will see this as a great peformance booster.

---

### Post by nephish on 2008-07-21
OK, lots to chew on, thanks. Made the swappiness to 0, was 10.
The filesystem is Ext3, with the default parameters you get with the xubuntu system. 

Will certainly look into these options for fstab.

Would getting the linux-kernel-2.yadda-server be a better kernel to have ? we do run a gtk program that brings the info into the database, other than that, we don't need much in the way of a GUI>

thanks again

---

### Post by gtdaqua on 2008-07-21
> 
The filesystem is Ext3, with the default parameters you get with the xubuntu system. 

You have plenty of room to make that server scream!

---

### Post by nephish on 2008-07-21
great, will try some of the kernel options after a bit more reading on them, also some mods in my fstab file. 
by the way, should i be using a different kernel? is there much difference from the xubuntu kernel (which i think is identical to the ubuntu one ) and the server kernel?

thanks for all your help.

---

### Post by windependence on 2008-07-21
Are you running 32 bit OS or 64? If you are running 32 bit, your OS can only address 4 gigs at a time even with PAE.

gtdaqua is right, there are so many things you can do to optimize your database, but you will have to buckle down, read the documentation, and learn to become a database expert in order to do that. It will not happen overnight. Second option, get a DB pro to come in and optimize your DB.

EXT3 can be tuned to go a lot faster but you will lose reliablility somewhat. If you have good UPS and good backups, I wouldn't worry about it.

-Tim

---

### Post by tinny on 2008-07-21
Ubuntu Server LTS Hardy optimizations.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

---

### Post by nephish on 2008-07-21
thanks, gents, for all your help, i have enough to research now. I am not sure i can run a 64 bit operating system on this box because the procs are not 64, jeez. Anyway. I will get into the filesystem and drives to see how much we can tune that up. 

Tanks again.

---

### Post by hyper_ch on 2008-07-21
how much caching of your queries do you have?

---

### Post by nephish on 2008-07-21
hey there all, here is my my.cnf I deleted the lines that were commented for brevity. There are some commneted lines regarding innodb ( which is what i use ), but i am not really familiar with what to put in each. 

well, here it is then
```

[client]
#password	= your_password
port		= 3306
socket		= /var/run/mysqld/mysqld.sock


[mysqld]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock
skip-locking
key_buffer = 384M
max_allowed_packet = 1M
max_connections = 300
table_cache = 512
sort_buffer_size = 2M
read_buffer_size = 2M
read_rnd_buffer_size = 8M
myisam_sort_buffer_size = 64M
thread_cache_size = 8
query_cache_size = 32M
thread_concurrency = 8

log-bin=mysql-bin

server-id	= 1

#tmpdir		= /tmp/		
#log-update 	= /path-to-dedicated-directory/hostname

#innodb_buffer_pool_size = 384M
#innodb_additional_mem_pool_size = 20M
# Set .._log_file_size to 25 % of buffer pool size
#innodb_log_file_size = 100M
#innodb_log_buffer_size = 8M
#innodb_flush_log_at_trx_commit = 1
#innodb_lock_wait_timeout = 50

log-slow-queries = /var/log/mysql/mysql-slow.log

[mysqldump]
quick
max_allowed_packet = 16M

[mysql]
no-auto-rehash
# Remove the next comment character if you are not familiar with SQL
#safe-updates

[isamchk]
key_buffer = 256M
sort_buffer_size = 256M
read_buffer = 2M
write_buffer = 2M

[myisamchk]
key_buffer = 256M
sort_buffer_size = 256M
read_buffer = 2M
write_buffer = 2M

[mysqlhotcopy]
interactive-timeout

```

Now the thing about the RAM, when i run an free -m, i usually get something like this.

         total       used       free         
Mem:     15738       4714      11024      

would this indicate that I am using more than 4 GB of RAM?

and i guess i am running the server kernel, here is my uname -a

2.6.22-15-server

OK, so thanks again. :)

---

### Post by gtdaqua on 2008-07-21
type "cat /proc/cpuinfo" and the in the output, see the "flags" section

```

**flags**           : fpu vme de pse tsc msr pae mce cx8 apic sep 
mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall
nx mmxext fxsr_opt rdtscp **lm** 3dnowext 3dnow
pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
 ts fid vid ttp tm stc

```

You should have "lm" flag listed for 64 bit capabilities.

---

### Post by nephish on 2008-07-21
thanks,
lm is not in the flags list.

---

