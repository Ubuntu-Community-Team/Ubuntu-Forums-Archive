---
title: "RSYNC + Crontab Tutorial using SSH or Daemon"
date: 2009-12-02
forum: Security
---

### Post by neilevan814 on 2009-12-02
[SIZE=4]**How To Backup Directories/Files on a Remote Machine & Local Machine using RSYNC and CRONTABS on UBUNTU 9.10 Karmic Koala and most likely Hardy & Jaunty **[/SIZE]
  
 This tutorial will show you how to run rsync using ssh to access the remote machine and an rsync daemon in order to access the remote machine.  Most people like to use ssh as it is the more secure way without a lot of fuss.  I have both methods installed on my machines and like them equally. 
  
 **REMOTE BACKUPS using RSYNC via SSH **
  
 [SIZE=1][I]This method will run backups on your local machine as root securely while not logged in as root. 
[/I][/SIZE]
  
 **FIRST:** Install on your local machine openssh-client ***<signed in as root>*** 
 $** apt-get update && apt-get install openssh-client** <or just use Synaptic Package Manager> 
  
         Install on your remote machine openssh-server*** <signed in as root> ***
 $** apt-get update && apt-get install openssh-server **<or just use Synaptic Package Manager> 
  
         [SIZE=3]_Now create a Public/Private Key pair in order to sign into the remote machine using ssh _[/SIZE]
 
 On your local machine  
  
 [SIZE=1]**root@localmachine$ mkdir ~/.ssh **[/SIZE]
 [SIZE=1]**root@localmachine$ chmod 700 ~/.ssh **[/SIZE]
 [SIZE=1]**root@localmachine ssh-keygen -q -f ~/.ssh/id_rsa -t rsa **[/SIZE]
 [SIZE=1]**Enter passphrase (empty for no passphrase): whateveryouliketo123say **[/SIZE]
 [SIZE=1]**Enter same passphrase again: whateveryouliketo123say **[/SIZE]
 
 [The file permissions should be locked down to prevent other users from being able to read the key pair data. OpenSSH may also refuse to support public key authentication if the file permissions are too open. These fixes should be done on all systems involved.] ref: [http://sial.org/howto/openssh/publickey-auth/ ]("http://sial.org/howto/openssh/publickey-auth/")
  
 **root@localmachine$ chmod go-rwx ~/.ssh/*** 
  
 Now it's time to get the public key over to the remote machine 
  
 **root@localmachine$ cd /root **
 **root@localmachine:~# ls -la  <look for the .ssh directory> **
 **root@localmachine:~# cd .ssh **
 **root@localmachine:~/.ssh ls  <look for the id_rsa.pub file> **
  
 [Now you will need a way to copy that file into the /root/.ssh directory on the remote machine.  I use a **usb key** to copy on to.  I will show you the way it is always advertised in all the other tutorials, but I think that only works if you can log into the remote already.{if I am wrong, please correct} 
 ***not sure if this works*** 
 scp ~/.ssh/id_rsa.pub server.example.org: 



  
 Here's a simple way to **copy onto a usb key using drag and drop: **
 Open a file browser as root: 
 **root@localmachine:~/.ssh# nautilus --no-desktop** _<or: gksudo nautilus> _
 That will bring you to the point of drag and drop      [SIZE=3]** or**[/SIZE]
 In the terminal: 
 **root@localmachine:~/.ssh# cp id_rsa.pub /media/<your usb key directory> **
  
 On the remote machine 
  
 **root@remotemachine$ mkdir ~/.ssh **
 **root@remotemachine$ chmod 700 ~/.ssh **
 **root@remotemachine$ <drag and drop like above into /root/.ssh>  or   **
 **root@remotemachine$ cat /media/<your usb key directory>/id_rsa.pub >> ~/.ssh/authorized_keys **
 **root@remotemachine$ chmod 600 ~/,ssh/authorized_keys **
  
 Now back to the local machine 
 [SIZE=2]You will need to check on the admin internet page for your router to find the internet address assigned to the remote machine  [/SIZE]
  
 Now that you have that address you can test to make sure root@localmachine can access root@remotemachine 
  
 **root@localmachine:~/ ssh [EMAIL="root@remote.addres"]root@remote.addres[/EMAIL]_s_**
 you will see alot of words and then yes or no :**type yes<enter> **
  
 Now you should see 
 **Enter passphrase for key 'root/.ssh/id_rsa': whateveryouliketo123say **
  
 Now you should be at this prompt<you may have to type your passphrase several times before.> 
  
 **root@<your-remote-computer-name>:~# **
  
 SUCCESS! 
  
  Type exit to return to the local prompt 
  
 **SECOND: **Install keychain on Debian / Ubuntu Linux ***<signed in as root> ***
 **This will be needed in order for root to be able to sign into your remote machine using a ssh passphrase 
  
 **$ apt-get update && apt-get install keychain **
  
 Now update your /root/.bashrc(in ubuntu) other flavors may use .bash_profile 
  
 **root@localmachine:~/# gedit .bashrc **or use _nano .bashrc _(for terminal editing) 
  
 Append the following to the bottom of the script:  
  
 This will allow keychain to be called at every login, at which point you will be prompted for the passphrase once and then while logged in it will be stored for use without having to re-enter the passphrase. <referenced[ http://www.cyberciti.biz/faq/ssh-passwordless-login-with-keychain-for-scripts/]("http://www.cyberciti.biz/faq/ssh-passwordless-login-with-keychain-for-scripts/")>


  
  
 **[SIZE=1]### START-Keychain ### [/SIZE]**
 **[SIZE=1]# Lets  re-using of ssh-agent and/or gpg-agent between logins [/SIZE]**
 **[SIZE=1]/usr/bin/keychain $HOME/.ssh/id_rsa [/SIZE]**
 **[SIZE=1]source $HOME/.keychain/<local machine name>-sh [/SIZE]**
 **[SIZE=1]#example $HOME/.keychain/neil-htpc-sh [/SIZE]**
 **[SIZE=1]### End-Keychain ### [/SIZE]**
 **[SIZE=1]###Keychain Security### [/SIZE]**
 [B][SIZE=2]#[SIZE=1]Allows only cron jobs to use passphrase-less logins when you are logged out 
[/SIZE][/SIZE][/B]
 **[SIZE=1]/usr/bin/keychain --clear $HOME/.ssh/id_rsa [/SIZE]**
 [SIZE=2]**[SIZE=1]###End-Keychain Security### [/SIZE]**
[/SIZE]
[SIZE=2]
[/SIZE]
  
 Now log into the remote machine once: 
 **root@localmachine:~/ ssh [EMAIL="root@remote.addres"]root@remote.addres[/EMAIL]s.#.#  **
  
 [SIZE=3]Logout to only grant access to cronjobs for ssh backups [/SIZE]
  
 [I][SIZE=2]Here is an **[SIZE=3]example backup script[/SIZE]** which backs up your selected directories and keeps a rotating set of 5 dated folders of backups which are just link images of the first backup directory with only the directory changes being hardcopied in.  This saves massive amounts of space and time for your backup jobs. I named this one dirsbackup.sh.  I saved it to /usr/local/bin/dirsbackup.sh then $ chmod +x /usr/local/bin/dirsbackup.sh .  This will make the script executable. Referenced [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/) and [http://ss64.com/bash/rsync.html ]("http://ss64.com/bash/rsync.html")
 ************************************************************ [/SIZE][/I]
  
 [SIZE=2]#!/bin/bash [/SIZE]
 **[SIZE=2]#Variable to point root to a Bash shell to execute the script(very important) [/SIZE]**
 [SIZE=2]ENV=/root/.bashrc [/SIZE]

#remount the drive as read-write
 #mount /media/backups -o remount,rw #optional

 **[SIZE=2]#Reference the source where the root passphrase is stored [/SIZE]**
 [SIZE=2]source /root/.keychain/neil-htpc-sh [/SIZE]

 **[SIZE=2]#Change to the directory where your backups will be kept [/SIZE]**
 [SIZE=2]cd /media/backups/192.168.1.3 [/SIZE]

[SIZE=2]**#create directory variable**
DestDir="/media/backups/192.168.1.3/"[/SIZE]

**[SIZE=2]#create date variables for backup days[/SIZE] in seconds**
 [SIZE=2]CurrentDate=`date +%s`
FiveLessDate=$(($CurrentDate-(86400*5)))

**#convert dates from seconds to human form**
strCurrent=`gawk 'BEGIN{print strftime("%Y-%m-%d",'$CurrentDate')}'`
strFiveLess=`gawk 'BEGIN{print strftime("%Y-%m-%d",'$FiveLessDate')}'`

**#check for day 5 folder and make if needed**
[ ! -d $strFiveLess ] && mkdir $strFiveLess

[/SIZE]**[SIZE=2]#rotate  day 5 backup images[/SIZE]**
 rm -rf $strFiveLess

 **[SIZE=2]#start rsync backups [/SIZE]**
  [SIZE=2]rsync --delete -az --rsh=/usr/bin/ssh root@192.168.1.3:/etc "$DestDir""$strCurrent"[/SIZE]
 [SIZE=2]rsync --delete -az --rsh=/usr/bin/ssh root@192.168.1.3:/root "$DestDir""$strCurrent"[/SIZE]
 [SIZE=2]rsync --delete -az --rsh=/usr/bin/ssh root@192.168.1.3:/usr "$DestDir""$strCurrent"[/SIZE]
 [SIZE=2]rsync --delete -az --rsh=/usr/bin/ssh root@192.168.1.3:/var "$DestDir""$strCurrent"[/SIZE]
 [SIZE=2]rsync --delete --exclude=.gvfs -az --rsh=/usr/bin/ssh root@192.168.1.3:/home/neil "$DestDir""$strCurrent" [/SIZE]
 [SIZE=2]rsync --delete -az --rsh=/usr/bin/ssh root@192.168.1.3:/tmp "$DestDir""$strCurrent"[/SIZE]

**[SIZE=2]#send email to notify of backup day completed[/SIZE]**
echo "Daily Backup Completed `date +%Y-%m-%d`" | mail -s "local.sh" user@localhost 

#remount drive read-only
 #mount /media/backups -o remount,ro #optional

  
 **[SIZE=2]#check if backup failed and document to /var/log/messages [/SIZE]**
 [SIZE=2][ $? -eq 0 ] && logger 'RSYNC Remote Directories Backup completed successfully' || logger 'RSYNC Remote Full Backup Failed' [/SIZE]
  
[CENTER]  [SIZE=2]**[SIZE=3]Local Backup Script[/SIZE]** [/SIZE]

[/CENTER]
 #!/bin/bash
**#Variable to point root to a Bash shell to execute the script**
ENV=/root/.bashrc

#remount the drive as read-write
#mount /media/backups -o remount,rw #optional

[SIZE=2]**#Change to the directory where your backups will be kept** [/SIZE]
DestDir="/media/backups/localfolders/"

**[SIZE=2]#create directory variable[/SIZE]**
cd $DestDir

**[SIZE=2]#create date variables for backup days[/SIZE] in seconds**
CurrentDate=`date +%s`
FiveLessDate=$(($CurrentDate-(86400*5)))
[B]
[SIZE=2]#convert dates from seconds to human form[/SIZE][/B]
strCurrent=`gawk 'BEGIN{print strftime("%Y-%m-%d",'$CurrentDate')}'`
strFiveLess=`gawk 'BEGIN{print strftime("%Y-%m-%d",'$FiveLessDate')}'`

**[SIZE=2]#check for day 5 folder and make if needed[/SIZE]**
[ ! -d $strFiveLess ] && mkdir $strFiveLess

**[SIZE=2]#rotate  day 5 backup images[/SIZE]**
rm -rf $strFiveLess

**[SIZE=2]#start rsync backup routine[/SIZE]**
rsync -az --delete /etc "$DestDir""$strCurrent"
rsync -az --delete --exclude=.gvfs --exclude=/your/files/toexclude  /home/user "$DestDir""$strCurrent"/home
rsync -az --delete /usr "$DestDir""$strCurrent"
rsync -az --delete /boot/grub/grub.cfg "$DestDir""$strCurrent"
rsync -az --delete /var "$DestDir""$strCurrent"

**[SIZE=2]#send email to notify of backup day completed[/SIZE]**
echo "Daily Backup Completed `date +%Y-%m-%d`" | mail -s "local.sh"  user@localhost                     

#remount drive read-only
#mount /media/backups -o remount,ro #optional

**[SIZE=2]#check if backup failed and document to  /var/log/messages [/SIZE]**
exit 0 && logger 'Local Backup completed successfully' || logger  'Local Backup Failed'


  
 *****************************************************************  
  
 [SIZE=3]**REMOTE RSYNC Backups Via Daemon **[/SIZE]
  
 This stuff gets done on the machine you want to take stuff off of(remote-machine) to backup onto the machine you are using(local-machine) to rsync  
  
 Create a file: "**/etc/rsyncd.conf**", with the contents referenced via [SIZE=2]terminal man 5 rsyncd.conf & man 1 rsync[/SIZE]) 



                  
                                                                                   
 **#Global Settings **
  
 **    uid = root **
 **    gid = root **
 **    read only = no **
 **    use chroot = no **
 **    pid file = /var/run/rsyncd.pid **
 **    lock file = /var/run/rsync.lock **
 **    transfer logging = true **
 **    log format = %h %o %f %l %b **
 **    log file = /var/log/rsyncd.log **
 **    list = yes **
 **    auth users = root **
 **    secrets file = /etc/rsyncd.secrets **
 **    hosts allow = 192.168.1.1 192.168.1.2 192.168.1.3 192.168.1.4 **
  
  
 **#Local Settings-Modules **
  
 **        [neil] **
 **        path = /home/neil **
 **        comment = Remote Backup **
  
 **        [root] **
 **        path = /root **
  
 **        [etc] **
 **        path = /etc **
  
 **        [tmp] **
 **        path = /tmp **
  
 **        [var] **
 **        path = /var **
  
 **        [usr] **
 **        path = /usr/local/bin **
  
 [B]        [full] = / 
[/B]

                                                                              
  
  
  
 Create a file: "**/etc/rsyncd.secrets**", with the contents: 
  **username:yourpassword**
   
 change permissions to[B] chmod 600 
[/B]

  
 [SIZE=3]**install xinetd **[/SIZE]
  
 edit **/etx/xinetd.d/rsync **
 

 add:
  
  **service rsync **
 **  { **
 **      disable         = no **
 **      socket_type     = stream **
 **      wait            = no **
 **      user            = root **
 **      server          = /usr/bin/rsync **
 **      server_args     = --daemon **
 [B]      log_on_failure  += USERID 
[/B]
 [B]  } 
[/B]

  
 restart xinetd.d 
 [B]/etc/init.d/xinetd restart 
[/B]

  
 edit 
 [SIZE=2]/etc/default/rsync [/SIZE]
 [B]RSYNC_ENABLE=inetd 
[/B]

  
 [SIZE=3]Now back to the local machine[/SIZE]
 Create a password file containing only the password that matches the password in the other machines /etc/rsyncd.secrets 
  
 call this file **/etc/rsyncd.password **
 **chmod 600 **
  
 Now you can set up a backup script just like the one above except use this format for your rsync commands: 
  
 **rsync --password-file=/etc/rsyncd.password --delete -az root@192.168.1.3::neil /media/backups/192.168.1.3/backup.0 **
  
 The difference being: 
 the use of --password-file=/etc/rsyncd.password & 
 the use of modules instead of directory calls.  So, instead of using the form root@192.168.1.3**:/home/neil** .... 
 you would use root@192.168.1.3**::neil** .... 
  
 If you review the rsyncd.conf file up above you will notice that there are modules in brackets [neil] and below a line showing the path to [neil] path=/home/neil 
  
 **LAST STEP: **Set Up Crontabs 
  
 **root@localmachine:~/ crontab -e **
  
 this will bring a message asking you which editor you want to use.  Choose **nano** It is the easiest. 
  
 Now you are in root's crontab -e 
  
 **# m h  dom mon dow   command **
 **00 00 * * *    /usr/local/bin/dirsbackup.sh **
 
 **00 01 1 * *   /usr/local/bin/fullbackup.sh **
  
 these entries will run dirsbackup.sh midnight(00 mins 00 hour) every day of month(dom) every month(mon) every day of the week(dow) In other words evry day at midnight 
  
 fullremote will run 1:00am (00 mins 01 hour - these are recorded in 24hr military time so 1:00pm is 00 13) first day of the month (1) every month(*) every week (*) 



  
 [SIZE=3]Here is a list of some special crontab functions:[/SIZE]
[SIZE=3]
[/SIZE]
  
 **evry 5 mins **
 ***/5 * * * * **
  
 **Emailing Cron Output: **
  
 **MAILTO="recipient@domain.com" **
 **MAILTO=""  <- will send no email **


  
**Special Strings **
  
 **These can be used to replace the 5 time values. **
  
 **string          meaning **
 **------          ------- **
 **@reboot         Run once, at startup. **
 **@yearly         Run once a year, "0 0 1 1 *". **
 **@annually       (same as @yearly) **
 **@monthly        Run once a month, "0 0 1 * *". **
 **@weekly         Run once a week, "0 0 * * 0". **
 **@daily          Run once a day, "0 0 * * *". **
 **@midnight       (same as @daily) **
 **@hourly         Run once an hour, "0 * * * *". **
  
 Also referenced [URL="http://content.hccfl.edu/pollock/Unix/Crontab.htm"]http://content.hccfl.edu/pollock/Unix/Crontab.htm 

[/URL]     That's It!  I hope this helps.  I had a rough time getting it all together for myself so knowing the pain I went through I wanted to spare others.

---

### Post by cariboo on 2009-12-02
I'll try your tutorial later, but why run it all as root? The root account is disabled for a reason.

---

### Post by neilevan814 on 2009-12-02
I run it as root because that is the only way I can backup directories owned by root  such as /etc /var /usr...
I have thoroughly researched this method and it is very secure.  Only cron is able to access root's permissions to ssh when you are logged out of root.

This way I do not have to be signed in as root all the time.  When you are signed out of root you need to include a variable ENV=/root/.bashrc to even get a shell for root to run ssh at all.

---

### Post by cariboo on 2009-12-02
Thank you for the explanation.

---

### Post by neilevan814 on 2009-12-03
Your Welcome.  And when you try it out..please let me know of any improvements that can be made.

I think getting this remote backup stuff together is really confusing, so if this is good, I want it to be really good.

---

### Post by Lars Noodén on 2009-12-04
> **neilevan814 said:**
> I run it as root because ...

Actually, it is not the only way to get at those directories.  You can make a separate account, just for backup, and then give sudo privileges to run rsync.  If you want to make it read-only, then watch the output from sshd to see how you are connecting and then cut-paste that into /etc/sudoers

You can lock down that backup account using sshd_config to ForceCommand.  Or you can make **authorized_keys**, **~/.ssh** and **~/** each read-only and *not* owned by that user, and then use **Command="..."** in the key itself.  

You'll need to use the argument **--rsync-path='sudo rsync'** with rsync on the client.  

And to get the exact rsync command to put into sudoers on the server, you'll need to have rsync run the ssh client in verbose/debug mode using **-e "ssh -t -v"**.  That will show up, somewhere, as a line something like this
```

debug1: Sending command: **sudo rsync --server --sender -e.iLs . /*yaddayadda...***

```

---

### Post by neilevan814 on 2009-12-05
This is great.  I will try to figure this out as well...but, I may just be dense right now but can you explain this a little more.  Can you use for my help...local machine and remote machine..client server always messes me up.  Here's the line.

You'll need to use the argument **--rsync-path='sudo rsync'** with rsync on the client.

---

### Post by Lars Noodén on 2009-12-05
> **neilevan814 said:**
> This is great.  I will try to figure this out as well...but, I may just be dense right now but can you explain this a little more.  Can you use for my help...local machine and remote machine..client server always messes me up.  Here's the line.

You'll need to use the argument **--rsync-path='sudo rsync'** with rsync on the client.

Ok.  The account on the **server** is named **bkupacct** and the private RSA key is ~/.ssh/**key_bkup_rsa** on the client.  On the **server**, the account **bkupacct** is a member of the group **autobackup**.

The public key, ~/.ssh/**key_bkup_rsa.pub**, has been copied to the account **bkupacct** on **server** and placed in ~/.ssh/authorized_keys there.  

The following directories on **server** are owned by root and belong to the group **bkupacct** and *not* group readable, but not group writeable, and definitely not world readable: "~" and "~/.ssh".  Same for the file "~/.ssh/authorized_keys" there.  (This assumes you are not also using ACLs)

```

# This is *one* way of many to set permissions on the **server**:
sudo chown root:**bkupacct** ~
sudo chown root:**bkupacct** ~/.ssh/
sudo chown root:**bkupacct** ~/.ssh/authorized_keys
sudo chmod u=rwx,g=rx,o= ~
sudo chmod u=rwx,g=rx,o= ~/.ssh/
sudo chmod u=rwx,g=r,o=  ~/.ssh/authorized_keys

```

Say you're backing up from **server** to **client**.  rsync on the client uses ssh to make the connection to rsync on the server. 

```

# rsync is invoked from **client** like this
# to see exactly what parameters are being passed to the server
rsync \
  -e "ssh \
         -i ~/.ssh/**key_bkup_rsa**  \
         -t             \
         -l **bkupacct**"   \
  --rsync-path='sudo rsync' \ 
  --delete   \
  --archive  \
  --compress \
  --verbose  \
  bkupacct@**server**:/etc \
  /media/backups/**server**/backup.0 

```

The argument **--rsync-path** tells the server what to run in place of rsync.  In this case it runs **sudo rsync**

The argument **-e** says which remote shell tool to use.  In this case it is **ssh**.  

For the **ssh** client being called by the **rsync** client, **-i** says which key, specifically, to use.  That is independent of whether or not an authentication agent is used for ssh keys.  Having more than one key is a possibility, since it is possible to have different keys for different tasks.

The rest,  --delete, --archive, --compress, --verbose, and the rest don't need explanation.

**sudo** will need to be configured on the **server**.  

```

%autobackup ALL=(ALL) NOPASSWD: rsync --server --sender -e.iLs . /etc/ *and so on...*

```

You can find the exact settings(s) to use in /etc/sudoers by running the ssh client in verbose mode on the **client**.  Keep making adjustments to /etc/sudoers on the **server** until it works as it should:

```

# rsync is invoked from **client** like this
rsync \
  -e "ssh \
         -i ~/.ssh/key_bkup_rsa  \
         -t                      \
         **-v**                      \
         -l bkupacct"            \
  --rsync-path='sudo rsync' \ 
  --delete   \
  --archive  \
  --compress \
  --verbose  \
  bkupacct@server:/etc \
  /media/backups/server/backup.0 

```

---

### Post by neilevan814 on 2009-12-05
Thanks a lot for the explanation.  I did not know you could put that sudo rsync option on the rsync command...very helpful.

---

### Post by neilevan814 on 2010-02-26
Hello Lars,

I hope you meander back this way...I finally got around to trying these non root autobackup routines.  I am having some problems I think in understanding :
1) Client or Server /etc/sudoers edit
2) Configuring the server 
%autobackup rsync --server --sender -e.iLs . /etc/ [I]and so on...
I really am not sure what I am supposed to do here
[/I]
I think it is this 2) that most likely is causing my impass.  Thanks, Neil

---

### Post by Lars Noodén on 2010-03-02
> **neilevan814 said:**
> Hello Lars,

I hope you meander back this way...I finally got around to trying these non root autobackup routines.  I am having some problems I think in understanding :
1) Client or Server /etc/sudoers edit


Server.

> **neilevan814 said:**
> Hello Lars,
2) Configuring the server 
%autobackup rsync --server --sender -e.iLs . /etc/ [I]and so on...
[/I]


Thanks for spotting that.  I've fixed the syntax for [sudoers](http://linux.die.net/man/5/sudoers) and use the full path to rsync.

Using the ssh client in verbose mode will tell you exactly which arguments are being sent to  the server.

---

### Post by neilevan814 on 2010-03-08
Thanks Lars for fixing the bit about  the sudoers list.  I am still a little unclear though.  What does the -e.iLs mean in the entry line
autobackup ALL=(ALL) NOPASSWD: rsync --server --sender -e.iLs . /etc/ *and so on.*
and does the list of files and directories to have sudo permissions follow after as in this case I am reading it as directories     . <space>/etc/<space>and so on....  is this right?

---

