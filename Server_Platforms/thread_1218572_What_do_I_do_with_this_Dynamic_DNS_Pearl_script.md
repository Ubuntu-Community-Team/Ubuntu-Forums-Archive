---
title: "What do I do with this Dynamic DNS Pearl script"
date: 2009-07-20
forum: Server Platforms
---

### Post by strujillo.jr on 2009-07-20
Ok so I found this script online that will work with updating my ip address with editDNS.net
Here it is.

This is what the guy said ::


Requirements:
1) You need to register first! (duh)
2) Donations are optional, but if it makes your life easier you should consider it and you’ll also get more services.
3) Perl!
File: editdns.pl

```
#!/usr/bin/perl
 
use strict;
 
## Configure ONLY this 2 variables
my $editdns_pass   = "a"; # put your password
my $editdns_record = "b"; # put the record you wish to update
 
## ###############
## Nothing else should be changed unless you know what to do
## ###############
 
my $host = "DynDNS.EditDNS.net";
my $port = 80;
my $editdns_post = "p=$editdns_pass&r=$editdns_record";
 
my $editdns_req = join("",
  "POST /api/dynLinux.php HTTP/1.0\r\n",
  "Host: $host:$port\r\n",
  "User-Agent: EditDNS Browser 0.1\r\n",
  "Referer: http://www.editdns.net\r\n",
  "Content-Type: application/x-www-form-urlencoded\r\n",
  "Content-Length: ".length($editdns_post)."\r\n\r\n",
  "$editdns_post\n"
);
 
my $hostaddr = (gethostbyname($host))[4] || &error("Couldn't get IP for $host");
my $remotehost= pack('S n a4 x8',2,$port,$hostaddr);
socket(S,2,1,6) || &error("Couldn't create socket");
connect(S,$remotehost) || &error("Couldn't connect to $host:$port");
select((select(S),$|=1)[0]);
print S $editdns_req;
vec(my $rin='',fileno(S),1)= 1 ;
select($rin,undef,undef,60) || &error("No response from $host:$port");
undef($/);
close(S);
print "[DONE]\n";
exit;
 
sub error {
        print "[ERROR] $_[0]\n";
        exit;
}
```
Next and once you have configured the script:
```
chmod +x editdns.pl
pico /etc/crontab
# Add editdns.pl to execute every 15 minutes
*/15 * * * * root /path/editdns.pl > /dev/null 2>&1

```

Ok so what do I do with it? Where do I type the code into? Where do i save it?
This is the page where I got it from [http://xux.in/blog/post/ip-updater-for-editdnsnet/]("http://xux.in/blog/post/ip-updater-for-editdnsnet/")

---

### Post by cariboo on 2009-07-21
Put the script in /usr/local/bin, and make sure it is executable, the create a cron job.

> chmod +x editdns.pl
pico /etc/crontab
# Add editdns.pl to execute every 15 minutes
*/15 * * * * root /path/editdns.pl > /dev/null 2>&1

The first line of the above quote tells you to make the script executable, the next line tells you to open /etc/crontab, using pico, pico isn't installed by default, but nano is, and add lines 3 and 4 to /etc/crontab. In Ubuntu the command would be:

```
sudo nano /etc/crontab
```

change /path/editdns.pl to /usr/local/bin/editdns.pl

---

### Post by strujillo.jr on 2009-07-21
Ok, sorry for being such a noob lol, but how do I put the script into /usr/local/bin. Also, do I need to install perl or anything. Thanks :-)

---

### Post by strujillo.jr on 2009-07-21
Nevermind i got it working. For anyone in the future that might read this all I did was type
First i installed perl like this. i dont know if this is 100% right but I got it off of a tutorial that was install perl so yeah...lol
```
udo aptitude install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl 
```
Then I said
```
sudo nano /usr/local/bin/editdns.pl
```
and then typed the code into there. Then once that was done I typed 
```
sudo chmod +x /usr/local/bin/editdns.pl
```
Then nothing happened, but dont freak out, that means it worked.
Finally I typed
```
sudo nano /etc/crontab
```
and then typed this at the bottom of the script
```
# Add editdns.pl to execute every 15 minutes
*/15 * * * * root /path/editdns.pl > /dev/null 2>&1
```
and finally just to make sure it worked I typed
```
perl /usr/local/bin/editdns.pl
```
and BAM! Like that it updated my IP address... :popcorn:

---

