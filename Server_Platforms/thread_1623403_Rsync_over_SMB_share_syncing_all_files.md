---
title: "Rsync over SMB share syncing all files"
date: 2010-11-16
forum: Server Platforms
---

### Post by hotpuppy on 2010-11-16
Hi,
  I'm having some trouble figuring out rsync and getting it to do what I want.  I need some help finding the settings that will result in the desired output.
 
I run a hybrid Windows, Linux / Ubuntu small business network.  I'm down to one Windows box actually.
 
I have a QNAS Linux based NAS
 
I have a Ubuntu "server" (atom based mobo) Tuxback.  
 
I have 3 inexpensive NAS devices.
 
These consitute a multi-tiered backup strategy that leverages rsync to provide real time data availability.
 
Basically a replica of the data is copied from the QNAS and Windows server to a folder called /backup
 
This part works reasonably well.
 
The QNAS shares are mounted with NFS.
The windows share is mounted via SMB.
 
I then replicate my data out to my inexpensive NAS devices, two of them are on-site and one is off-site.  I'm running CN-390 CoolMax devices which use Embedded linux.
 
The challenge is these are "stupid" devices and I can't install rsync to them....so I'm using them via SMB shares mounted in Fstab.
 
The problem I'm having is that when rsync runs on Tuxback it is copying from /backup to /linux/NAS1 (where NAS1 is mounted).
 
It sees this as "local" and disables partial file transfer and starts copying all of the data all over again.
 
I've read the manpage and I've googled for ideas.  
 
The command being run is:
rsync -rDltzv --delete /backup /linux/nas1
 
What am I doing wrong?
 
Btw, this started out as an inexpensive alternative to off-site storage and was based on a "cluster" of 1 TB Atom-based Ubuntu Servers..... After about a year I decided to downgrade to NAS because it's a responsible way to manage power, the NAS's are small, inexpensive, and my remote user can understand "is the light flashing?  press the button to turn it off, press it again to turn it on"
 
The new devices are about $150 USD for the device and a 2 TB HDD and pull under 50 watts.
 
The result is that I have a RAID config on my servers that protects against HW outages.  
 
The replica on Tuxback protects against the delete key which is the most common reason you need a backup.
 
The replica on NAS1 and NAS2 (warehouse and backoffice) protect against flood/fire/theft.  As a NAS is very tiny it's unlikely to be stolen assuming they even spotted it.
 
The offsite replica protects against Acts of Religious Diety (Flood Tornado Hurricane Visit from Angry Celestial Being)
 
The end result is under $1000 which is affordable for my small business.
 
I chose rsync because I could get it going *now* and manage it.... I'd like to upgrade to Zmanda, but that's a tall rosebush to climb and I haven't had time to sit down and get my head around it.
 
Rsync should be able to copy only the changes but it doesn't seem to be doing this.
 
Oh, I forgot to add, all of my machines are sync'd to the QNAS device which is sync'd to an external credible source.
 
And the NAS devices have the second option of FTP for access, but I chose SMB as it seemed simpler and I don't recall if rsync works with ftp.... of course being linux rsync could probably be made to work with the kitchen sink with the right script.

---

### Post by dtfinch on 2010-11-16
I'd add a "--modify-window=3605" to better skip files where the times and sizes don't change. The 3600 (1 hour) is because daylight savings causes windows and some other SMB servers to misreport times by an hour. The extra 5 seconds is because SMB times are rounded. Without at least a few seconds window it would always recopy most files when the source or destination is a windows/smb server.

Partial-file updates aren't going to be possible without rsync running on both the client and server. Though there is "Duplicity" which I've never used that can do partial file backups to a dumb remote server. The destination server won't have a mirror of the data but rather a series of encrypted daily rdiff patches that when merged together would equal the current data.

---

### Post by hotpuppy on 2010-11-18
Thank you for the suggestion and explanation about the --modify-window option.
 
I tried that and got a new error...
[EMAIL="root@tuxback:/"]root@tuxback:/[/EMAIL]# rsync -rDltzv --delete --modify-window=3065 /backup //nasw/backup
sending incremental file list
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: mkdir "//nasw/backup" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

Not sure what the issue is..... but it isn't related to the option.

[EMAIL="root@tuxback:/"]root@tuxback:/[/EMAIL]# cd /linux/nasw
[EMAIL="root@tuxback:/linux/nasw"]root@tuxback:/linux/nasw[/EMAIL]# ls
backup
[EMAIL="root@tuxback:/linux/nasw"]root@tuxback:/linux/nasw[/EMAIL]#

the directory exists..... and it's [EMAIL="accessibleroot@tuxback:/linux/nasw/backup"]accessibleroot@tuxback:/linux/nasw/backup[/EMAIL]# ls
accounting  asterisk-etc    asterisk-usr  bizfiles    chron             graphics    marshafiles  software  ups
archive     asterisk-spool  asterisk-var  brianfiles  database-backups  kevinfiles  robertfiles  tscfiles  webdata
[EMAIL="root@tuxback:/linux/nasw/backup"]root@tuxback:/linux/nasw/backup[/EMAIL]#
 
 
And I can write/delete there:

[EMAIL="root@tuxback:/linux/nasw/backup"]root@tuxback:/linux/nasw/backup[/EMAIL]# touch stupid
[EMAIL="root@tuxback:/linux/nasw/backup"]root@tuxback:/linux/nasw/backup[/EMAIL]# ls
accounting  asterisk-etc    asterisk-usr  bizfiles    chron             graphics    marshafiles  software  tscfiles  webdata
archive     asterisk-spool  asterisk-var  brianfiles  database-backups  kevinfiles  robertfiles  stupid    ups
[EMAIL="root@tuxback:/linux/nasw/backup"]root@tuxback:/linux/nasw/backup[/EMAIL]# rm stupid
[EMAIL="root@tuxback:/linux/nasw/backup"]root@tuxback:/linux/nasw/backup[/EMAIL]#
 
 
hmmm, this worked the other day.... [pull hair] grrr [/pull hair]
 
Have I done something wrong in mounting?
//nasw/backup on /linux/nasw type cifs (rw,mand)
//nas1/backup on /linux/nas1 type cifs (rw,mand)
//oms/webdata on /windows/oms/webdata type cifs (rw,mand)
//nas2/backup on /linux/nas2 type cifs (rw,mand)

Relevant portion of fstab

#nas boxes
//nas1/backup /linux/nas1 smbfs credentials=/home/brian/.nascredentials
//nas2/backup /linux/nas2 smbfs credentials=/home/brian/.nascredentials
//nasw/backup /linux/nasw smbfs credentials=/home/brian/.nascredentials

---

### Post by hotpuppy on 2010-11-18
What baffles me is that I have permissions, I can manually access it, but rsync fails hard.....
 
rysnc vvvvv   :
 rsync -rDltzvvv --delete /backup //nasw/backup/

tail end of the output
[sender] make_file(backup/accounting/Accounting/AP/2010/Terms Vendors/Broder/Oct10/06Oct10.pdf,*,2)
[sender] make_file(backup/accounting/Accounting/AP/2010/Terms Vendors/Broder/Oct10/14Oct10.pdf,*,2)
[sender] make_file(backup/accounting/Accounting/AP/2010/Terms Vendors/Broder/Oct10/20Oct10.pdf,*,2)
[sender] make_file(backup/accounting/Accounting/AP/2010/Terms Vendors/Broder/Oct10/28Oct10.pdf,*,2)
server_recv(2) starting pid=3621
received 1 names
recv_file_list done
received 19 names
recv_file_list done
get_local_name count=20 //nasw/backup/
rsync: mkdir "//nasw/backup" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
[Receiver] _exit_cleanup(code=11, file=main.c, line=595): about to call exit(11)
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
[sender] _exit_cleanup(code=12, file=io.c, line=601): about to call exit(12)

---

### Post by dtfinch on 2010-11-18
Shouldn't it be /linux/nasw/ not //nasw/backup/ ?

---

### Post by hotpuppy on 2010-11-18
:o
 
There are some days I feel like a cat in a 4 dog fight.  Yes, I was attempting to "solve" this problem by using UNC style shares.... two days ago when I last looked at the issue.  I guess I didn't undo my "fix" and I couldn't for the life of me figure out why it wasn't working.... of course I was trying to have a "quick" look at it over my lunch in between the typical daily fires that I deal with.... Nothing like the call from the customer in the lobby who forgot to tell you they needed something at 11am instead of 5pm that day.

---

### Post by hotpuppy on 2010-11-18
I always say that we are trying to protect ourselves from the delete key..... and the "last command" function.
 
So now that I've corrected that issue.....

[EMAIL="root@tuxback:/linux"]root@tuxback:/linux[/EMAIL]# rsync -rDltzvv --delete --modify-window=3605 /backup /linux/nasw
sending incremental file list
delta-transmission disabled for local transfer or --whole-file
backup/
backup/accounting/
backup/accounting/Accounting/
deleting backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.5dYBgs
backup/accounting/Accounting/PPThumbs.ptn
backup/accounting/Accounting/TFI condensed15 Jan 05.QBB
 
 
Notice it's trying to copy this file ... that is dated Jan 05, which hasn't changed since then.
 
I turned up the vvv and resubmitted it.....

[generator] make_file(backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.caTr3T,*,2)
delete_item(backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.caTr3T) mode=100755 flags=2
deleting backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.caTr3T
recv_generator(backup/accounting/Accounting/PPThumbs.ptn,30)
send_files(30, //backup/accounting/Accounting/PPThumbs.ptn)
send_files mapped //backup/accounting/Accounting/PPThumbs.ptn of size 9922

 
I don't understand the internals of rsync... but it looks to me like the program is deleting the file and then sending it.... 
 
a little further up there is something that makes me wonder if time is not being set properly

set modtime of backup/accounting/Accounting to (1288761029) Wed Nov  3 00:10:29 2010
delete_in_dir(backup/accounting/Accounting)

 
Here is the offending file:

-rwxr-xr-x 1 root root      9922 2010-11-12 13:03 PPThumbs.ptn
-rwxr-xr-x 1 root root 112775103 2010-11-12 13:04 TFI condensed15 Jan 05.QBB
-rwxr-xr-x 1 root root     15360 2010-11-12 13:04 Thumbs.db
 
Here is the output on a re-run:

[generator] make_file(backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.vnhQhT,*,2)
delete_item(backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.vnhQhT) mode=100755 flags=2
deleting backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.vnhQhT
recv_generator(backup/accounting/Accounting/PPThumbs.ptn,30)
send_files(30, //backup/accounting/Accounting/PPThumbs.ptn)
send_files mapped //backup/accounting/Accounting/PPThumbs.ptn of size 9922
calling match_sums //backup/accounting/Accounting/PPThumbs.ptn
backup/accounting/Accounting/PPThumbs.ptn
sending file_sum
false_alarms=0 hash_hits=0 matches=0
sender finished //backup/accounting/Accounting/PPThumbs.ptn
recv_generator(backup/accounting/Accounting/TFI condensed15 Jan 05.QBB,31)
send_files(31, //backup/accounting/Accounting/TFI condensed15 Jan 05.QBB)
send_files mapped //backup/accounting/Accounting/TFI condensed15 Jan 05.QBB of size 112775103
calling match_sums //backup/accounting/Accounting/TFI condensed15 Jan 05.QBB
backup/accounting/Accounting/TFI condensed15 Jan 05.QBB

 
Am I reading the output wrong or is it retransmitting the file each time?

---

### Post by dtfinch on 2010-11-18
The "delete_item(backup/accounting/Accounting/.TFI condensed15 Jan 05.QBB.caTr3T)" looks like it's deleting a partial file a previous aborted transfer. Rather than directly overwriting existing files, rsync copies to a new file, then renames it over the old file when its done, to prevent it from corrupting existing files if the connection is lost mid-transfer.

You've verified that "TFI condensed15 Jan 05.QBB" has the same size and date on both sides?

---

### Post by hotpuppy on 2010-11-18
There is definately a time sync issue living here....
 
total 110180
drwxr-xr-x 1 root root         0 2010-11-12 19:14 AP
drwxr-xr-x 1 root root         0 2010-11-12 19:14 AR - 4 years
drwxr-xr-x 1 root root         0 2010-11-12 19:14 Bank and Card Statements - 5 years
-rwxr-xr-x 1 root root     23040 2010-11-12 13:04 credit references.doc
drwxr-xr-x 1 root root         0 2010-11-12 19:14 Customer Files
drwxr-xr-x 1 root root         0 2010-11-12 19:14 Financials
drwxr-xr-x 1 root root         0 2010-11-12 19:14 Fixed Assets
drwxr-xr-x 1 root root         0 2010-11-12 19:14 Marsha
-rwxr-xr-x 1 root root        77 2010-11-12 13:04 maxdesk.ini
drwxr-xr-x 1 root root         0 2010-11-12 19:14 POs
-rwxr-xr-x 1 root root      9922 2010-11-12 13:03 PPThumbs.ptn
-rwxr-xr-x 1 root root 112775103 2010-11-12 13:04 TFI condensed15 Jan 05.QBB
-rwxr-xr-x 1 root root     15360 2010-11-12 13:04 Thumbs.db
[EMAIL="root@tuxback:/linux/nasw/backup/accounting/Accounting"]root@tuxback:/linux/nasw/backup/accounting/Accounting[/EMAIL]# cd /backup/accounting/Accounting/
[EMAIL="root@tuxback:/backup/accounting/Accounting"]root@tuxback:/backup/accounting/Accounting[/EMAIL]# ls -l
total 110332
drwxr-xr-x  6 root root      4096 2010-11-03 00:21 AP
drwxr-xr-x  6 root root      4096 2010-11-03 00:10 AR - 4 years
drwxr-xr-x 17 root root      4096 2010-11-03 00:14 Bank and Card Statements - 5 years
-rw-r--r--  1 root root     23040 2008-06-03 10:26 credit references.doc
drwxr-xr-x  4 root root      4096 2010-11-03 00:09 Customer Files
drwxr-xr-x  2 root root      4096 2010-11-03 00:10 Financials
drwxr-xr-x  3 root root      4096 2010-11-03 00:08 Fixed Assets
drwxr-xr-x  9 root root      4096 2010-11-03 00:08 Marsha
-rw-r--r--  1 root root        77 2009-09-04 16:32 maxdesk.ini
drwxr-xr-x 14 root root      4096 2010-11-03 00:10 POs
-rw-r--r--  1 root root      9922 2008-05-21 15:37 PPThumbs.ptn
-rw-r--r--  1 root root 112775103 2005-01-19 21:22 TFI condensed15 Jan 05.QBB
-rw-r--r--  1 root root     15360 2007-06-05 15:14 Thumbs.db

This is immediately after the sync.  Appears that my NAS devices are using the present time..... and my server is using the original file date.....
 
Do I have an option wrong in this command?
rsync -rDltzvvv --delete --modify-window=3605 /backup /linux/nasw

---

### Post by hotpuppy on 2010-11-18
Well, I decided to try the --size-only option and that does work.... so now it's just a matter of trying to determine why the CN-390 devices from coolmax won't allow the time to be set.
 
Of course the better option would be NFS and an Rsync server......
 
Granted it's an ARM processor and embedded linux... but it should be capable.
 
 
Anyhow, are there any other options I should consider besides --size-only?

---

### Post by dtfinch on 2010-11-19
If you have the space, I'd suggest the -b (backup) and --backup-dir options, so that it just moves old files rather than actually deleting them. That way if everything disappeared from the production server one day, it wouldn't get deleted from the backup servers on the next backup.

You also have some unnecessary options, though they probably won't make much difference. -D is just for copying devices and other special files. -l is for copying symlinks. -z is for compression which only works when rsync is connecting to another instance of itself.

Other things to check:
If the return code from rsync is greater than zero, you'd probably want your script to alert you somehow. "if [ $? -gt 0 ]; then ..."
I'd have the script check that all shares are properly mounted, so /backup doesn't get emptied if the QNAS or Windows servers fail to mount (making the source an empty directory), and so the backup server doesn't fill itself up if nas1/2/w fail to mount. I run "mount | grep name" which returns 0 if found, 1 if not found.

---

### Post by hotpuppy on 2010-11-19
Great suggestions.... thank you.  I will implement the logic in the scrip when I get a little better at scripting.  I'm reading a book on bash scripting right now so that I can improve my scripting abilities.  Right now I'm just simply running rsync via the command line.... as most of the machines (QNAS, tuxback, Windows) are on the same hub there isn't as much risk.  However, the two local replicas (nas1/2) are elsewhere in the building, and Nasw will be remote.... so checking mount status is a great idea.
 
I need to think through the backup option..... not sure how much space we need yet as the replication hasn't fully completed due to the time issue.
 
I emailed coolmax about it.... also asked them for NFS and rsync support... it is after all a linux machine so it should be able to do anything linux can do and an Arm processor should be able to handle rsync if it can handle disk/network io.

---

### Post by hotpuppy on 2010-11-19
One other question...
 
What's the right way to kill rysnc processes via script?
 
I kick these off at various times at night, but they slow the network down... so I need them gone by 8:05am.  I'm using crontab and killall rsync right now....  Is there a better way?

---

### Post by dtfinch on 2010-11-19
I have a short list of alternating "killall -9 rsync" and "sleep 10", in case the backup script starts another rsync after the first is killed.

---

