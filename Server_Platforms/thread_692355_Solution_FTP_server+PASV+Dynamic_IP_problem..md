---
title: "Solution: FTP server+PASV+Dynamic IP problem."
date: 2008-02-09
forum: Server Platforms
---

### Post by einstein on 2008-02-09
For all those folks that have been trying to get a world accessible ftp server running on their LAN and who have a dynamic IP address, here is what I have found.

FIRST, PLEASE NOTE:  Almost everything here must be done as root.  This can be dangerous.  If you are not sure of something, don't do it unless you choose to risk the integrity of your system.  I have been running the perl script and the cron job for a couple of days now without any problems.  That may not be the case on your computer.  To wit, I have installed software from the Ubuntu repositories that really messed up my system.  Not because there was anything wrong with the software but, rather, because I could not figure out how to configure it properly for my system.  Please see [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48).

By the way, if someone spots something here that really is dangerous, or even just a bad idea, I sure would like to know.

I will make this into a howto of sorts.  While I solved the problem using vsftpd, I suspect it works for proftpd and others.  Thing is, it is not really a server problem; it is more of a networking problem.

The actual problem is that, after the active (and usually successful) login, the ftp server says let's go passive and sends its IP address, or what it thinks it is, to the client.  If this does not jive with what the FTP client got from it's initial DNS lookup, the client will look like it is hanging forever waiting for the file listing.  What it is really doing is igoring everything from what it considers a bogus server joining the conversation while it waits for a response from the server it contacted originally.

So, do this:
[LIST=1]
[*]Get a domain name from as site like dynDNS.
[*]Implement a script (I used perl) to query your router and get the current gateway dotted IP address.  Alternatively, query [http://corz.org/ip](http://corz.org/ip).  You have to parse the data in either case but the latter is probably easier.
[*]In the same script, compare the current IP address to the pasv_address in vsftpd.conf.  If they are different, modify vfstpd.conf.  Here's my perl script, /etc/vsftpd/pubipmon, owned by root::
```
#!/usr/bin/perl -w
#
##	User Beware! !!!! DISCLAIMER !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
#	
#	Anyone may do anything at anytime with this script EXCEPT hold me responsible
#	for any damages, incurred any time or any where by anyone, that might somehow
#	be related to the use of this script.
#	
#	I have only a rudimentary knowledge of perl.  I am self taught out of need
#	to get things done - I don't care about pretty; I care about functionality.
#	I am NOT an EXPERT programmer.  My code is, and will be considered to be,
#	ugly by some.  However, along with being functional, it is human readable - 
#	mostly so I can easily figure what the Hell I did if I look at the code
#	sometime down the road.  This is a good thing for a guy that normally
#	cannot remember what day it is.
#	
#	There you have it.  Beware, be warned, take heed and even write it down
#	somewhere, the creator of this perl script cannot, and will not, be held
#	responsible for anything.
##	!!!!!!!!!!!!!!!!! DISCLAIMER !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
#
#	A script to monitor router public IP address (gateway).  The talktoRouter
#	sub is specific to a DLink DI-824VUP with firmware version 1.05.
#	It does this:
#		- monitor's public IP address
#		- rewrites the ftpd conf file, if necessary
#		- e-mails someone to say what adversity it encountered
#		- other stuff not programmed yet
#
#	Run it with cron with something like:
#	0,10,20,30,40,50 * * * * root /etc/vsftpd/pubipmon >> /var/log/pubipmon.log
#	This runs the script every 10 minutes every hour of every day of every month
#	on every day of the week.
 
################################################################################
#	Set some variables:
#
#	Should not need $tmp_file. Should be able to parse the LWP::UserAgent
#	$res->as_string directly but I cannot get it to happen.
	$tmp_file= '/etc/vsftpd/status.txt';
	
#	$log_file is for reference only - print output is piped to the log file in  
#	the $log_file = '/var/log/pubipmon.log';	#	cron command.
#	Make sure this matches YOUR system.
	$FTPdConf = '/etc/vsftpd/vsftpd.conf';

#	Specify your router connection variables.
	$RouterAdmin='your router admin user ID';
	$RouterPWD = 'your router admin passwood';
	$RouterURL='http://your router IP:port/could be status.htm';

#	To get e-mail notifications...
	$smtpserver = "your.smtp.server";
	$Mailto = "<you\@your.email";
	$Mailfrom = "pubipmon \<pubipmon\@your.email\>";	#	Make up something legit.
	$Sender = $Mailfrom;
	$Cc = "soneone.else\@somewhere.else";	#In case you need other's to know
	$Subject = "Pub IP Notice";
	$MailMsg="";	#	We fill this as we go.

#	Just so the don't turn up !defined somewhere.
	$currentIP="";	
	$oldIP="";		

#	E-mail notification should be optional.
	$Mailme = 1;	#	0 for no mail. 1 to send mail.

################################################################################
#	Okay, let's roll...
	print &TheTime,"\tStarting poll...\n";	# optional

	if(&getLastIP){	#	Read and parse $FTPdConf for currently used pasv_address
		undef $ret;		#	- I think its MasqueradeAddress for proftpd
		if(&talktoRouter){
			undef $ret;
			if(&parseRouterResponse){
				undef $ret;
				if(&compareIPs){
					undef $ret;
					if($currentIP ne $oldIP){
						undef $ret;
						&modifyConf;
					}
				}
			}
		}
		else{	#	Down and dirty way to retry &talktoRouter if it failed firt time.
			if(&talktoRouter){
				undef $ret;
				if(&parseRouterResponse){
					undef $ret;
					if(&compareIPs){
						undef $ret;
						if($currentIP ne $oldIP){
							undef $ret;
							&modifyConf;
						}
					}
				}
			}
		}
	}
	else{	#	Failed to read or understand $FTPdConf.
		print &TheTime,"\t\$getLastIP failed.\n";
	}

	if ($Mailme == 1 && $MailMsg ne ""){
		&emailit($MailMsg);
	}

	print &TheTime,"\tFinished\n";	#	optional.

	exit;
##*********************************************************
##*********************************************************
sub getLastIP{
	print &TheTime,"\tGetting oldIP...";
	if(open(CONF,"$FTPdConf")){
		@tmp = <CONF>;
		close CONF;
		chomp @tmp;
		foreach $tmp(@tmp){
			if ($tmp =~ /^pasv_address/){	#	Modify this for other ftpd programs.
				($option,$oldIP) = split(/\=/,$tmp);	#	Same here.
			}
		}
		if ($oldIP ne ""){
			print " Success\n";
			$ret = 1;
		}
		else{
			$MailMsg = "$MailMsg\nUnable to extract old IP from $FTPdConf";
			print &TheTime,"\tUnable to extract old IP from $FTPdConf. ";
			print "Tidying up and exiting.\n";
			$ret=0;
		}
		
	}
	else {
		print " Failed. Unable to open $FTPdConf to extract old IP: $!\n";
		$MailMsg = "$MailMsg\nUnable to open $FTPdConf to extract old IP: $!";
		$ret=0;
	}
	return $ret;
}
sub talktoRouter{		#Get $RouterURL and store it in $tmp_file.
	print &TheTime,"\tTalking to router....";
	use LWP::UserAgent;
	
	$ua = new LWP::UserAgent;
	$req = new HTTP::Request GET => $RouterURL;
	#	Next line only needed if you set an admin password on your router.
	$req->authorization_basic($RouterAdmin,$RouterPWD);
	
	
	$res = $ua->request($req);
	if ($res->is_success ){  
		open(SRC,">$tmp_file");	
		print SRC $res->as_string;	
		close SRC;
		$ret = 1;
		print "\n";
	}
	else	{
		$MailMsg = "$MailMsg\nRouter wouldn't talk to us: $!";
		print " Failed. Router wouldn't talk to us: $!\n";
		$ret = 0;
	}
	return $ret;
}

sub parseRouterResponse{
	print &TheTime,"\tParsing router response....";
	if (open(SRC,"$tmp_file")){
		@data = <SRC>;
		chomp @data;
		close SRC;

#	Begin router dependent! Search your router's status page's source for clues.
		$getnext=0;	#	I used the clue in the line preceding the data I wanted.
		foreach $data (@data){
			if ( $data =~ /<B>Gateway<\/B>/ ){	#	The clue.
				$getnext=1;		# Found the clue so parse the next line.
			}
		 	elsif ($getnext==1){
		   	$data =~ s/<TD>//g;		# trim extraneous tags
		   	$data =~ s/<\/TD>//g;	# trim extraneous tags
		   	$currentIP = $data;
				$getnext=0;		#	Parsed the next line so turn this off.	
  			}
		}
#	End router dependent!.

		if ($currentIP eq ""){
			$MailMsg = "$MailMsg\nUnable to extract IP from $tmp_file";
			print " Failed. Unable to extract IP from $tmp_file\n";
			$ret=0;
		}
		else{
			print "\n";
			$ret = 1;
		}
	}
	else {
		print " Failed. Could not open $tmpfile for parsing: $!\n";
		$MailMsg = "$MailMsg\nCould not open $tmpfile for parsing $!";
		$ret = 0;
	}
	return $ret;
}

sub compareIPs{
	print &TheTime,"\tComparing public IPs....";
	if($currentIP eq $oldIP){
		print " No public IP change so cleaning up and leaving.\n";
		$ret=0;	#Not an error condition - just prevents further processing.
	}
	else{
		print " Changed.\n";
		$ret=1;
	}
	return $ret;
}

sub modifyConf{
	print &TheTime,"\tModify $FTPdConf....";
	if(open(CONF,"$FTPdConf")){
		@Conf = <CONF>;
		close CONF;
		chomp @Conf;
		foreach $line(@Conf){
			if ($line =~ /^pasv_address/){	#	Modify this for other ftpd programs.
				($option,$value) = split(/\=/,$line);
				$line = "$option\=$currentIP";
			}
		}
		if (open(CONF,">$FTPdConf")){	#	Save the modified $FTPdConf.
			foreach $line(@Conf){
				print CONF $line,"\n";
			}
			$MailMsg = "$MailMsg\nModified $FTPdConf";
			close CONF;
		}
		$ret = 1;
	}
	else{
		print " Failed. $FTPdConf NOT MODIFIED!: $!\n";
		$MailMsg = "$MailMsg\n$FTPdConf NOT MODIFIED!: $!";
		$ret = 0;
	}	
	return $ret;
}

sub emailit{
	print &TheTime,"\tEmailing....$Mailto to advise\n";
	use MIME::Lite;

	$Message = shift(@_);

	$mailer = MIME::Lite->new(
		From=>$Mailfrom,
		To=>$Mailto,
		Sender=>$Sender,
		Cc=>$Cc,
		Subject=>$Subject,
		Type=>'auto');
	$mailer->attach(
		Type=>'text',
		Data=>$Message);
	$mailer->send('smtp', $smtpserver);
	
}

sub TheTime{
	use Time::Local;

	($second, $minute, $hour, $dayOfMonth, $month, $yearOffset, $dayOfWeek, $dayOfYear, $daylightSavings) = localtime();
	$year = 1900 + $yearOffset;
	$month++;	#	$month is zero based so fix it.

#	I prefer yyyy-mm-dd hh:mm:ss so the rest of this just formating $ret.
	$theyear = "$year";
	if($month <10){$themonth = "0$month";}	
	else{$themonth = "$month";}
	if($dayOfMonth < 10){$theday = "0$dayOfMonth";}	
	else{$theday = "$dayOfMonth";}

	if($hour <10){$thehour = "0$hour";}	
	else{$thehour = "$hour";}
	if($minute <10){$theminute = "0$minute";}	
	else{$theminute = "$minute";}
	if($second <10){$thesecond = "0$second";}	
	else{$thesecond = "$second";}

	$ret = "$theyear\-$themonth\-$theday
 	$thehour\:$theminute\:$thesecond";
	return $ret;
}

```
[*] Run the script as a cron job - I use webmin so it is brain dead simple to set it up.  Run as root (there's probably a better user but I haven't figured out who it is) frequently - mine goes every 10 minutes.  Not because my dynamic IP address changes that frequently.  Rather, because in the remote event I try to access my ftp server shortly after an address change, I don't want to hang around waiting for very long.

My cron entry.  Print statement output is sent to /var/log/pubipmon.log
```

0,10,20,30,50 * * * * root /etc/vsftpd/ipmon >> /var/log/pubipmon.log

```
[*]Do /etc/init.d/vsftpd reload .... but how?  Use something like monit ([http://www.tildeslash.com/monit/who.php](http://www.tildeslash.com/monit/who.php)).  I used config howto at [http://www.howtoforge.com/server_monitoring_monit_munin_p2](http://www.howtoforge.com/server_monitoring_monit_munin_p2). It's in the Gutsy repository; probably others as well.  By the way, the monit web interface is at: [http://localhost:2812](http://localhost:2812), if you uncomment and don't change the default monitrc setting.  Don't forget to edit /etc/default/monit when configuring.
[*]Use monit to Monitor the vsftpd.conf timestamp.  When it changes, kuzz yer script modified it with the new gateway address, have monit do exec /etc/init.d/vsftpd reload.

Here is the relevant part of my monitrc - this is actually complete enough for monit to start (with /etc/init.d/monit restart):
```

# /etc/monit/monitrc
set daemon  120	#	seconds between checks.
set logfile syslog facility log_daemon
set mailserver your.smtp.server		#	Change to suit YOU.
set mail-format { from: you@your.email }
set alert root@localhost		#	Change to suit YOU.
set httpd port 2812 and
#     SSL ENABLE
#     PEMFILE  /var/certs/monit.pem
     allow adminUID:adminPPWD		#	Change to suit YOU.

#check process proftpd with pidfile /var/run/proftpd.pid
#   start program = "/etc/init.d/proftpd start"
#   stop program  = "/etc/init.d/proftpd stop"
#   if failed port 21 protocol ftp then restart
#   if 5 restarts within 5 cycles then timeout

check process vsftpd with pidfile /var/run/vsftpd/vsftpd.pid
   start program = "/etc/init.d/vsftpd start"
   stop program  = "/etc/init.d/vsftpd stop"
   if failed port 21 protocol ftp then restart
   if 5 restarts within 5 cycles then timeout

check file vsftpd.conf with path /etc/vsftpd/vsftpd.conf
   if changed timestamp
      then exec "/etc/init.d/vsftpd reload"

```
[/LIST]

I will post a sanitized version of my vsftpd.conf soon.

Hope this helps someone.

Best regards,
                Dennis

---

### Post by stock1232 on 2008-02-20
Wow this is some work. I have the same problem with FTP and Dynamic IP problem. I tried to follow your code but have no clue how to implement it. 

I have the ddclient running to update my IP. I installed it from the repositories. I think it is similar to this. Is there a way you could do a simliar how to? Like create folder here. Copy this code into a text file here.

---

### Post by einstein on 2008-02-20
Hi, Stock1232;

I am not sure how ddclient works or what artifacts it produces to record activity - I use the built in update client my DLink router.

The overall objective is simple - find out if your public IP address has changed and, if so, tell vsftpd.conf and then do a vsftpd reload.

Have a look in  /var/cache/ddclient/ddclient.cache and see what gets recorded.  You should be able to extract your current public IP address and then rewrite vsftpd.conf if the current address is different than the pasv_address value.  I use monit to monitor the time stamp on vsftpd.conf and do a vsftpd reload if the time stamp changes.

In any case you will need to implement some scripting to get the job done as automatic rewrites to any conf file are, AFIK, very unusual.

Hope this helps.  If you could post your ddclient.cache file, I might be able to help you with the actual perl script you would need to get everything done.

Regards,
    Dennis

---

### Post by stock1232 on 2008-02-21
Thanks for the reply. Here is the config for cache

## ddclient-3.7.3
## last updated at Sat Feb 16 13:53:38 2008 (1203191618)
atime=1203191017,backupmx=0,custom=1,host=amswebsitedesign.com,ip=66.146.211.16,mtime=1203191017,mx=,static=0,status=good,warned-min-error-interval=0,warned-min-interval=0,wildcard=0,wtime=30 amswebsitedesign.com

If you could help me write the script which compares ip to pasv_address and if its different change pasv_address to change to ip address.

Thank you, Thank you

---

### Post by stock1232 on 2008-02-25
Dennis,

Can we take your script from above and modify it? Instead of monitoring your routers IP address we monitor the ddclient.cache file for changes. Then the rest of the code to rewrite and reload vsftpd would be the same?

Thanks

---

### Post by einstein on 2008-02-25
HI, stock1232;

First, my apologies on not getting back to you sooner - I have been doing battle with a client's upset industrial wastewater plant.  I did finally figure out how to get 48 hours into day but I can still only get 3.5 of them into a week.

You may do anything you wish with my script.  It is quite modular.  One thing to note is that, by default with vsftpd, you get /etc/vsftpd.conf.  This was awkward for me so I created /etc/vsftpd/ and created a sym link to /etc/vsftpd.conf.

Otherwise, reading the script from top to bottom, the first sub that needs modification is talktoRouter.  You want to "talkto" your cache file instead.

The next sub, parseRouterResponse, would be silly for your case (actually it's silly in mine too but I couldn't get a more correct method to work) - you could just parse your cache file while still in your talktoRouter equivalent.

The rest of the script should need little change.  You will need to modify some variables at the top of the script.  You will also need to modify the program execution steps to accomodate your changes around talktoRouter and parseRouterResponse.

Finally, my script does not reload vsftpd - I implemented monit to do this, as shown in my howto.  monit monitors the timestamp on vsftpd.conf and reloads vsftpd IF the timestamp has changed.

Hope this helps.

Best regards,
               Dennis

---

### Post by stock1232 on 2008-02-26
Dennis,

Can you check the attachment to see if my code makes sense?

Thanks,

Drew

---

### Post by einstein on 2008-02-26
Hi, Drew;

Yes, the code looks pretty good.  The only issue that I can see would be in the getCacheIP sub in the 'foreach $Ctmp(@Ctmp)' loop.  Based on the cclient cache file you posted a while back,.it appears the everything is on one continuous line.  If the following is the full extent of the typical file...
```
## ddclient-3.7.3
## last updated at Sat Feb 16 13:53:38 2008 (120319161
atime=1203191017,backupmx=0,custom=1,host=amswebsi tedesign.com,ip=66.146.211.16,mtime=1203191017,mx= ,static=0,status=good,warned-min-error-interval=0,warned-min-interval=0,wildcard=0,wtime=30 amswebsitedesign.com

```
... then the data you want is on the third line.  You could use a regex (best way but I am not good at at) or do something like the following..
```

sub getCacheIP{
	print &TheTime,"\tGetting IP from Cache...";
	if(open(CACHE,"$DDclient")){
		@Ctmp = <CACHE>;
		close CACHE;
		chomp @Ctmp;
                @Cbits = split(/\,/,$Ctmp[2]); #grab third line of file

#		foreach $Ctmp(@Ctmp){
#			if ($Ctmp =~ /^ip/){	#	Modify this for other ftpd programs.
				($option,$currentIP) = split(/\=/,$Cbits[4]);	#	Want fifth comma separated name=value pair.
#			}
#		}
		if ($currentIP ne ""){
			print " Success\n";
			$ret = 1;
		}
		else{
			print &TheTime,"\tUnable to extract old IP from $DDclient. ";
			print "Tidying up and exiting.\n";
			$ret=0;
		}
		
	}
	else {
		print " Failed. Unable to open $DDclient to extract current IP: $!\n";
		$ret=0;
	}
	return $ret;
}


```

You will notice that I added a line just before the foreach loop, commented out the foreach loop and modified the third line of the foreach loop.

You should be able to test your setup now with the above revisions added.  Don't forget that modification of vsftpd.conf has to happen as root.

Regards,
           Dennis

---

### Post by stock1232 on 2008-02-27
Dennis,

First of all, Thanks for all the help. I ran into another challanage

I installed monit. Copied your config like so making the proper adjustments.
Code:

# /etc/monit/monitrc
set daemon  60	#	seconds between checks.
set logfile syslog
set mailserver 127.0.0.1		#	Change to suit YOU.
set alert root@localhost		#	Change to suit YOU.
set httpd port 2812 and
#     SSL ENABLE
#     PEMFILE  /var/certs/monit.pem
allow localhost     
allow admin:test		#	Change to suit YOU.


check process vsftpd with pidfile /var/run/vsftpd/vsftpd.pid
   start program = "/etc/init.d/vsftpd start"
   stop program  = "/etc/init.d/vsftpd stop"
   if failed port 21 protocol ftp then restart
   if 5 restarts within 5 cycles then timeout


check file vsftpd.conf with path /etc/vsftpd.conf
   if changed timestamp
      then exec "/etc/init.d/vsftpd reload"

I then changed /ect/default/monit

# Defaults for monit initscript
# sourced by /etc/init.d/monit
# installed at /etc/default/monit by maintainer scripts
# Fredrik Steen <stone@debian.org>

# You must set this variable to for monit to start
startup=1

# To change the intervals which monit should run uncomment
# and change this variable.
CHECK_INTERVALS=60
[/CODE]

Then tried to start monit I get this:

drew@ubuntudevelopmentserver:~$ /etc/init.d/monit start
Starting daemon monitor: empty config, please edit /etc/monit/monitrc.

---

### Post by einstein on 2008-02-27
Hi, Drew;

Hmmmm.... no idea but it looks like monit cannot find its config (monitrc) where it thinks it should be.

Got it!  You need to do as super user:
```
sudo /etc/init.d/monit start
```


Regards,
       Dennis

---

### Post by stock1232 on 2008-02-28
You are the man!!! Thank you.

Ok monit is working.

I have my pubipmon (perl program) saved at /ect/vsftpd/pubipmon 

I created a log file (pubipmon.log) and put it in my file system at /var/log/pubipmon.log

I then need to run the program as a cron job. So I think in my file system the custom cron jobs are run at /etc/cron.d  Under that directory I found two files php5 and anacron. Under /etc i found cron.weekly, cron.daily, cron.monthly. I would not put the job there becaue I want it to run every 10 mins like yours does. So I added a file in /etc/cron.d called cronpubip. In there I put the code:
```

# /ect/cron.d/cronpubip deamon to change vsftpd IP address

# run the check every 10 mins
0,10,20,30,50 * * * * root /etc/vsftpd/pubipmon >> /var/log/pubipmon.log
```

If this was working properly, (testing) wouldn't my perl file print to /var/log/pubipmon.log regardless of my IP address changing? Because the file pubipmon.log is still blank. How did you test your system when you first started?

Thanks,

---

