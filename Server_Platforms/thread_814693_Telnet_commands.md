---
title: "Telnet commands"
date: 2008-05-31
forum: Server Platforms
---

### Post by quikone8 on 2008-05-31
I have tried in vain to find information on Net::Telnet.  When I try to search the forum, I get a multitude of forum errors when i try to search for anything with those two words.  I am trying to run the following script, but cannot figure out what I need to do it.  I have Telent and Tenet-utils.  Anyone have some direction for me?  By the way I ma running Server 8.04.

#!/usr/bin/perl -w
use strict;
use Net::Telnet ();
 
my ($s);
my $t = new Net::Telnet;
 
my $user = 'admin';
my $pass = 'xxxxxxxx';
my $fl = 'vcard';
my $target = 'Global Address Book';
 
$t->open(Host => 'localhost', Port => 504);
$s = $t->getline;
$t->print("USER $user");
$s = $t->getline;
$t->print("PASS $pass");
$s = $t->getline;
$t->print("GOTO $target");
$s = $t->getline;
 
$t->print('ENT0 1|||4');
$s = $t->getline;
$t->print('Content-type: text/x-vcard; charset=UTF-8');
$t->print("\n");
 
open(IN, "<$fl");
while (<IN>)
{
 if (/^$/)
 {
  $t->print('000');
  $t->print('ENT0 1|||4');
  $s = $t->getline;
  $t->print('Content-type: text/x-vcard; charset=UTF-8');
  $t->print("\n");
 }
 else
 {
  if (/FN:/)
  {
   my @name = split(/:/,$_);
   print "Adding $name[1]";
  }
 $t->print("$_");
 }
}
 
$t->print('000');
close(IN);
 
exit;

---

### Post by HermanAB on 2008-06-01
Telnet is deprecated.  Use SSH.

---

### Post by quelx on 2008-06-01
Did you install the **libnet-telnet-perl** package which contains the **Net::Telnet** module?

---

### Post by pdwerryhouse on 2008-06-01
> **HermanAB said:**
> Telnet is deprecated.  Use SSH.

I wish people would stop immediately saying "TELNET IS BAD. USE SSH", when someone asks a question about telnet. It doesn't answer the poster's question. It's not even vaguely helpful in this situation.

Telnet is *not* deprecated. Yes, its traffic is sent in cleartext and that's not good. But there are still plenty of devices around that have no remote access to them other than via telnet, and in some situations, the user might find this acceptable. Furthermore, the telnet command is used in debugging all the time.

To the original poster, the script works fine for me (well, except that I don't know what sort of service is supposed to be on port 504, so obviously it's not connecting to anything). As other people have pointed out here, you need the **libnet-telnet-perl** package.

---

### Post by quelx on 2008-06-01
> **pdwerryhouse said:**
> I wish people would stop immediately saying "TELNET IS BAD. USE SSH", when someone asks a question about telnet. It doesn't answer the poster's question. It's not even vaguely helpful in this situation.

Telnet is *not* deprecated. Yes, its traffic is sent in cleartext and that's not good. But there are still plenty of devices around that have no remote access to them other than via telnet, and in some situations, the user might find this acceptable. Furthermore, the telnet command is used in debugging all the time.

Agreed, in this case its used to move vcard information into a groupware application, **citadel**

[http://www.citadel.org/doku.php/faq:favoriteclient:migrating_ldap_into_citadel](http://www.citadel.org/doku.php/faq:favoriteclient:migrating_ldap_into_citadel)

---

### Post by quikone8 on 2008-06-01
Thanks to all that have replied to this post, all the info has been helpful.  I did install libnet-telnet-perl and still cannot fiqure out why I can't get the telnet commands to work.  Any other ideas?

---

### Post by quelx on 2008-06-01
Did you paste the script into a file (say *citadel.pl*?

how are you trying to run it?

```
perl citadel.pl
```

Are you able to telnet from the console of your citadel box?

```
telnet localhost 504
```

---

### Post by quikone8 on 2008-06-01
No, I have not pasted it to any file.  I have tried to run it from Konsole and Terminal, is that what I am doing wrong?  

Second question, yes it does work well.

---

### Post by quelx on 2008-06-01
copy and paste the script into a file change the ```
my $user = 'admin';
my $pass = 'xxxxxxxx';
my $fl = 'vcard';
my $target = 'Global Address Book';
``` lines to match your installation (use Kate, since you appear to be in KDE), it's arbitrary, but for the sake of sanity, save that file as **citadel.pl**

In konsole navigate to directory where you saved the **citadel.pl** and ```
perl citadel.pl
``` if it does not go as you expected paste what you see here (don't paste your password/username info)

---

### Post by quikone8 on 2008-06-01
Another question please, where do I store the file with the vcard file?

---

### Post by quelx on 2008-06-01
> **quikone8 said:**
> Another question please, where do I store the file with the vcard file?

Given ```
my $fl = 'vcard';
```, put it in the same directory as the script and call it vcard, I think.

---

### Post by quikone8 on 2008-06-02
am running the following script to import my 1900 + contacts into the global address room.  I am getting stuck on line 28, as indicated.

#!/usr/bin/perl -w
use strict;
use Net::Telnet ();
 
my ($s);
my $t = new Net::Telnet;
 
my $user = 'ron';
my $pass = 'rgp1953';
my $fl = '/media/disk address.vcf';
my $target = 'Global Address Book';
 
$t->open(Host => 'localhost', Port => 504);
$s = $t->getline;
$t->print("USER $user");
$s = $t->getline;
$t->print("PASS $pass");
$s = $t->getline;
$t->print("GOTO $target");
$s = $t->getline;
 
$t->print('ENT0 1|||4');
$s = $t->getline;
$t->print('Content-type: text/x-vcard; charset=UTF-8');
$t->print("\n");
 
open(IN, "<$fl");
while (<IN>)                *************8THIS IS THE AREA THE PROGRAM STICKS IN***********
{
 if (/^$/)
 {
  $t->print('000');
  $t->print('ENT0 1|||4');
  $s = $t->getline;
  $t->print('Content-type: text/x-vcard; charset=UTF-8');
  $t->print("\n");
 }
 else
 {
  if (/FN:/)
  {
   my @name = split(/:/,$_);
   print "Adding $name[1]";
  }
 $t->print("$_");
 }
}
 
$t->print('000');
close(IN);
 
exit;

Following is the message I get when I run the script:  readline() on closed filehandle IN at citadel.pl line 28.

 

Following is an example of the file I amattempting to import:  

 

BEGIN:VCARD
EMAIL:coldinco@comcast.net
N:Ann;Ann Bomgaars;;;
UID:006oPNgA2n
VERSION:3.0
END:VCARD
 
BEGIN:VCARD
EMAIL:jamioe@mediatrunk.c0m
N:Jamie;Jamie Wilkie;;;
UID:00oNifbsb0
VERSION:3.0
END:VCARD
 
BEGIN:VCARD
EMAIL:lwbeck@juno.com
N:Lorrie;Lorrie Beck;;;
UID:03BDB06LqO
VERSION:3.0
END:VCARD
 
BEGIN:VCARD
EMAIL:callie.wilburn@fotf.org
N:Callie;Callie Wilburn;;;
UID:05ioyWWvap
VERSION:3.0
END:VCARD

Thanks in advance for your suggestions.

---

### Post by quelx on 2008-06-03
> my $fl = '/media/disk address.vcf';

If this is indeed what you have in your perl script, then it needs to have a '**/**' (forward slash) between **disk** and **address.vcf** (you are loading your **.vcf** data file from an external drive, yes?):
```
my $fl = '/media/disk[SIZE="4"]**/**[/SIZE]address.vcf';
```

Let me know how it goes.

---

### Post by quikone8 on 2008-06-04
It works, but I get blank data.

---

### Post by quelx on 2008-06-04
> **quikone8 said:**
> It works, but I get blank data.

Have you tried contacting the script's author?

---

