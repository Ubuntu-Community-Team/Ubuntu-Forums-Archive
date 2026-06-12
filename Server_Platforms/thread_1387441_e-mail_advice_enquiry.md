---
title: "e-mail advice enquiry"
date: 2010-01-21
forum: Server Platforms
---

### Post by wvw on 2010-01-21
Hello All

I have a server running ubuntu 8.10. I have monitoring software to monitor cerain devices on our LAN & WAN. However I need to set up e-mail on the server to mail me alerts for when something goes down.

However this is where the problem comes in. I have never set up any mail clients on ubuntu server and am also not sure which one to use in this case. I have done some reading on squirrel mail and fetchmail. I am also aware there is roundcube and a few others available. 

Here's my scenario: We have a mail server located off site. We use XP with Outlook on all our work machines. Outlook connects to the mail server using https with basic ntlm auth.

So what I am trying to do is set up mail software to allow my server to send me an e-mail (using the above mail server) to my mail address so I get a mail whenever there's a problem with any of the devices being monitored.

Any suggestions or advice will be much appreciated.

Many Thanks
willemvw

---

### Post by steven.jones on 2010-01-21
Sendmail or postfix should do this fine....you just need a MTA (mail transfer agent) The application then calls the MTA which mails to your remote email server....this is a very std thing for Linux/Unix servers...

---

### Post by ian dobson on 2010-01-22
Hi,

What monitoring software are you using? If it supports sending emails on errors, just setup it up so that it sends emails to your mail server.

I use munin to monitor my server an just use this script to send warnings/errors to my email server:-

```

#!/usr/bin/perl
use Net::SMTP;
use Time::Local;

  my $MailServer="alpha2";
  my $MailTo='XXX@YYY';
  my $MailFrom='Munin@ZZZ';
  my $StandardIn="";
  our @day_abbrev = qw(Sun Mon Tue Wed Thu Fri Sat);
  our @month_abbrev = qw (Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec);

  my ($sec,$min,$hour,$dmon,$mon,$year,$wday,$yday,$isdst) = localtime(time());
  $year = $year + 1900;
  my $swday = $day_abbrev[$wday];
  my $smon = $month_abbrev[$mon];
  if ($sec < 10 ){$sec="0".$sec}
  if ($min < 10 ){$min="0".$min}
  if ($hour < 10 ){$hour="0".$hour}
  if ($dmon < 10 ){$dmon="0".$dmon}
  if ($mon < 10 ){$mon="0".$mon}

  my $Dte = "Date: $swday, $dmon $smon $year $hour:$min:$sec +0100";
 
  while (<STDIN>) {
    $StandardIn .= $_;
  }
 
  $smtp = Net::SMTP->new("$MailServer",
                    Hello => "$MailServer",
                    Timeout => 60,
                    Port    => 10025);
  $smtp->mail($MailFrom);
  $smtp->to($MailTo);
  $smtp->data();
  $smtp->datasend("$Dte\n");
  $smtp->datasend("Message-ID: <$sec$min$hour$dmon$mon$year$wday$yday$isdst\@alpha.planet-ian.com>\n");
  $smtp->datasend("From: $MailFrom\n");
  $smtp->datasend("To: $MailTo\n");
  $smtp->datasend("Subject: Email from alpha2\n"); 
  $smtp->datasend("\n");
  
  $smtp->datasend($StandardIn);
  $smtp->datasend("\n\n\n");
  $smtp->datasend;
  $smtp->quit;


exit;

```

Regards
Ian Dobson

---

### Post by FGuin on 2010-01-22
Hi.

You need to read about postfix or exim. I prefer exim... It works great with mysql virtual users.

---

