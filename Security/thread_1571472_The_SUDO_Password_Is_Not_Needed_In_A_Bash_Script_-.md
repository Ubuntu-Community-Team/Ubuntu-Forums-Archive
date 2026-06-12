---
title: "The SUDO Password Is Not Needed In A Bash Script ---&gt; Is This Normal?"
date: 2010-09-09
forum: Security
---

### Post by AlexanderDGreat on 2010-09-09
Hi, can you help me understand this? I have a server. I add this line in my /etc/crontab

```
0 17 * * * bart sh /media/backups/backup.sh
```

It backups files Everyday at 5PM - on a ext4 separate hard drive, backup.sh looks like this:

```
-rwxr--r-- 1 bart  bart  994 2010-09-10 04:13 backup.sh
```

I'm using RSYNC to backup my MBR, /boot, and /(root). Here's the script:

```
#backup mbr
**sudo** dd if=/dev/sda of=/media/backups/mbr/lgv-server_mbr bs=512 count=1

#backup /boot
**sudo** rsync -avz --delete /boot/ /media/backups/boot/

#backup /(root)
**sudo** rsync -avz --delete / /media/backups/root/
```

Did you notice I put **sudo** in there? Why? Because if I don't use SUDO, _root-owned-files_ won't get copied/backedup - right?

So I use SUDO. However, why doesn't it ask for a Password? I'm asking because I've seen people doing additional work just for a script to use SUDO. For example, editing the /etc/sudoers file, and putting there your User Name w/ NOPASSWD and PATH-to-your-script.

But me, I don't. I just put there SUDO + (command), and it has ALL the privilege of SUDO.

Not that I don't like this, but is this Normal? Shouldn't it ask for a password? Is this a SECURITY issue?

Why is this so? Is there something I need to understand about crontab, scripts, permissions in scripts, rsync, what have you or None?

Can you help me? Thanks for reading.

---

### Post by endotherm on 2010-09-09
its my understanding that cron runs as root, so all processes it spawns will also run as root. since crontab is owned by root, only someone who is already root can create a job, unless it is extended to users manually. the sudo command doesn't require a password, because the "shell" cron creates is already running as root. same as when you run two sudo commands in the same terminal within 15 minutes. 


this is why seperate config is needed to extend cron capabilities to normal users.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)  (see section "Enable User Level Cron")

```
Lucid:~$ ll /usr/bin  | grep crontab
-rwxr-sr-x  1 root   crontab   31656 2010-04-14 19:29 crontab*

```if you want to confirm it yourself, add a long running cronjob (a minute or so), and while it is running, run ps -ef and look at the user associated with your job. it should be root or an account that runs with equal priv.

---

### Post by CharlesA on 2010-09-09
It would be easier to drop sudo and just throw the backup script in the root's crontab.

How were you adding it to the crontab?

I do daily scans on my RAID array as a script in my crontab and it uses my user. The backup I run from a root crontab, runs as root.

Also, as a general rule, sudo doesn't normally work in cron, since it's run in the background with no prompt.

EDIT: It won't write to root-owned files, but normally you can read them just fine.

---

### Post by AlexanderDGreat on 2010-09-10
@endotherm - I figured out why. You're absolutely right. I didn't know I was entering my sudo password left & right, I thought that it wasn't needed in a bash script.

Now I know IT'S NEEDED. Thanks for the tip.

@CharlesA - Yes I dropped all the sudo in my bash script.

So here's what I did. Run sudo /etc/crontab - so it will run commands with SUDO privileges. Make the script owned by root (optional).

Then your script won't ever ask for your password, and at the same time you get sudo privileges inside that script. Now you're safe and DROP all sudos in that script.

Thanks guys. You're a ton of help when I was figuring this out! :)

---

### Post by The Cog on 2010-09-10
> **AlexanderDGreat said:**
> So here's what I did. Run sudo /etc/crontab - so it will run commands with SUDO privileges. Make the script owned by root (optional).

As a security measure, the script should be owned by root and only writable by root. Since it is running under root account, if anyone else could write it they would be able to do anything they like as root. Even you shouldn't be able to edit it without using sudo, just in case your account gets compromised.

---

### Post by AlexanderDGreat on 2010-09-12
Thanks The Cog. I have a question though...

I put this in my /etc/crontab:

```
0 17 * * * root sh /backups/backup.sh
``` Then...

```
-rwxr--r-- 1 root  root  994 2010-09-10 04:13 backup.sh
``` - I change owner to ROOT right?

**But I also tried taking out the "x" so it will NOT execute, but it still Executed!** Is this normal? Can you help my confusion?

The permission of the file now is -rw-r--r--.

---

### Post by The Cog on 2010-09-12
I would not expect the script to be able to execute if it is not marked as executable. Bear in mind though that you can still run an interpreter on text files even if they're not executable, as it is the interpreter that is executing and the script is merely its data. See this:
> steve@StevesPC:~$ ls -l test
-rw-r--r-- 1 steve steve 21 2010-09-12 18:46 test
steve@StevesPC:~$ cat test
echo test says hello
steve@StevesPC:~$ ./test
bash: ./test: Permission denied
steve@StevesPC:~$ sh test
test says hello


---

### Post by AlexanderDGreat on 2010-09-12
> I would not expect the script to be able to execute if it is not marked as executable. Bear in mind though that you can still run an interpreter on text files even if they're not executable, as it is the interpreter that is executing and the script is merely its data.

Oh I see. So do you suggest anything I change in my /etc/crontab or backup.sh? Or is everything ok and don't worry anymore?

:)

---

### Post by AlexanderDGreat on 2010-09-13
Just as Ubuntu's anacron command for the folders of /etc/cron.daily hourly weekly monthly, What's the **-x** for in /etc/crontab?

```
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

What do you think?

---

### Post by AlexanderDGreat on 2010-09-13
I think it's better to use (command) -x VS sh script.sh, this way, the former really follows that the file is executable.

---

### Post by endotherm on 2010-09-13
it's my understanding that root can read/write/execute a file with 000 permissions. 
```

Lucid:~$ echo hello > test1.txt
Lucid:~$ cat test1.txt
hello
Lucid:~$ chmod 000 ./test1.txt
Lucid:~$ ll | grep test1.txt
----------   1 user user     6 2010-09-13 10:38 test1.txt
Lucid:~$ sudo cat test1.txt
[sudo] password for user:
hello
Lucid:~$ 

```

---

### Post by CharlesA on 2010-09-13
Indeed. root has magic powahs!

---

### Post by The Cog on 2010-09-14
No. I don't think root has the power to execute non-executables. I just tried it. Like this:
```
echo echo It ran > test
./test
sh test
```
Same results whether root or not.

---

### Post by endotherm on 2010-09-14
> **The Cog said:**
> No. I don't think root has the power to execute non-executables. I just tried it. Like this:
```
echo echo It ran > test
./test
sh test
```Same results whether root or not.
hmmm, your right. I guess being able to chmod any file is sufficient for making sure root doesn't get locked out.

---

