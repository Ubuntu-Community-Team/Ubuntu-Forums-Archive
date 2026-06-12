---
title: "Setting up postfix for outgoing mail"
date: 2011-07-27
forum: Server Platforms
---

### Post by sneakyimp on 2011-07-27
I'm setting up a server and trying to make it *very* secure.  Before I configured my web stack, I was about to install some security packages, Tiger and Samhain, but these packages wanted to install sendmail so that they can send outgoing notifications. From the reading I've been doing, I believe I want postfix instead of sendmail.  It is my (perhaps mistaken) belief that installing postfix first will prevent them from installing this sendmail I do not want.

I want to install postfix with the following goals in mind:
* let PHP scripts send mail using the [mail]("http://php.net/mail") function.
* various system notification functions (cron, etc.) will be able to send their emails
* emails destined for root@localhost will be redirected to [email]admin@mydomain.com[/email]
* let tiger and/or samhain send their notification emails
* NO INCOMING OR LOCAL MAIL IS PERMITTED.  Because mail for my domain is handled by google apps, nobody will be checking mail on this server. Also, this server has very limited disk space. It is therefore very important that we don't have mail accumulating in boxes that will never be checked.
* no unnecessary ports, services, or cron jobs are running.  

I've been reading a [variety](https://help.ubuntu.com/community/Postfix) [of](https://help.ubuntu.com/community/PostfixAmavisNew) [pages](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto) that describe postfix setup on Ubuntu but these articles are imprecise, incomplete, and describe installation of things I don't want like POP/IMAP/etc.

There's also one final wrinkle.  I will be [setting up postfix to send via Amazon SES](http://docs.amazonwebservices.com/ses/latest/DeveloperGuide/index.html?IntegratingWithServer.Postfix.html).

If anyone can help me sort this, I'd very much like any tips or suggestions you may have.

---

### Post by sneakyimp on 2011-07-27
I've been looking into this and, unless I'm mistaken, this is what I should be doing:
[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client)

If anyone could corroborate that, I'd appreciate it.

I'm also wondering if this should also be done so that root@localhost actually gets sent to [email]root@mydomain.com[/email]:
[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#fantasy](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#fantasy)

---

### Post by HermanAB on 2011-07-28
Howdy,

Most all modern mail systems include a sendmail stub for legacy compatibility.  So if you install Postfix, Zimbra or Citadel, you will also have a little program called sendmail, which isn't really sendmail, but which will make other programs that want sendmail work.

You can either go to the Postfix home page and spend a week or two reading and experimenting, or you can install Citadel (in the repos) and have everything working in about 20 minutes.  Your choice!

---

### Post by sneakyimp on 2011-07-28
I installed postfix and tweaked the settings according to those links.  What I'm having trouble with now is connecting postfix to Amazon SES.  I seem to be missing some perl module:
```

user@host:/opt/third-party/amazon$ sudo ./ses-verify-email-address.pl -e https://email.us-east-1.amazonaws.com -k /opt/third-party/amazon/aws-credentials -v address@mydomain.com
Can't locate object method "ssl_opts" via package "LWP::UserAgent" at SES.pm line 250.


```

---

### Post by slochewie on 2011-07-28
I started working on this yesterday.
I think this should fix your problem:

As root or using sudo:
perl -MCPAN -e 'install LWP::Protocol::https'

Edit * That should be two sets of colons and a capital P but it put a smiley face....


I'm currently going through the README for those Amazon SES Perl scripts to see which ones I can get to install using apt-get and which ones you have to install from CPAN. 
You definitely have to do the above one through CPAN as far as I can figure out so far.

I think these PERL modules are installed with the corresponding deb packages. Not positive yet because I'm working on this as I type:

Digest::SHA -> libdigest-sha-perl
URI::Escape -> liburi-perl
Crypt::SSLeay -> libcrypt-ssleay-perl
XML::LibXML -> libxml-perl

I haven't figured out yet if there is deb package that can be installed via apt-get for Bundle::LWP and MIME::Base64
I don't think you have to worry about Bundle::LWP though.

I'm trying to get most of them done with apt-get because CPAN is interactive so it's not super easy to install all of those from a script and run it unattended.

I need to give credit to this guy too :)
[http://www.evanhoffman.com/evan/2011/04/28/integrating-amazon-simple-email-service-with-postfix-for-smarthost-relaying/](http://www.evanhoffman.com/evan/2011/04/28/integrating-amazon-simple-email-service-with-postfix-for-smarthost-relaying/)
Differing from his directions I copied SES.pm to /usr/lib/perl5/

Using the CPAN installer I've gotten it to work on a test machine. I still need to automate the install so I can recreate it on multiple production servers and do it all hands free.

---

### Post by sneakyimp on 2011-07-28
I truly appreciate your information.  I ran through all the crazy install processes yesterday -- so many dependencies stacked on dependencies.

Anyway, I have the scripts more or less working, but SES is rejecting the emails generated by my system on the basis of either missing or illegal headers.  It's SO ANNOYING.  For instance it rejects email if
* You have Precedence or Auto-Submitted headers.  There's a kludge that changes them to X-Precedence and X-Auto-Submitted instead
* You are missing a Subject header.  I don't know if there's any way I can enforce this system-wide.  
* You've got some other header or email property that results in an "undisclosed-recipients:;" being assigned somewhere.  I can't figure out what this header might be.

More information here:
[https://forums.aws.amazon.com/thread.jspa?messageID=264813&tstart=0](https://forums.aws.amazon.com/thread.jspa?messageID=264813&tstart=0)

Skip down to the last couple of posts (these are all mine) and you'll see the latest irritations.  Any advice you have would be much appreciated.  I'm wondering if there's something I can do in my postfix config to remove certain headers and add other default headers, but I haven't made any traction.

I'm also wondering how the amazon perl scripts might be modified to set a default and/or remove bad headers.

---

### Post by slochewie on 2011-08-01
[http://www.rackspace.com/knowledge_center/index.php/Postfix_-_Using_Telnet_to_Test_Postfix](http://www.rackspace.com/knowledge_center/index.php/Postfix_-_Using_Telnet_to_Test_Postfix)

I used those instructions to successfully send a test message.
Differing commands I used from that howto:
telnet localhost 25
EHLO localhost

I think I was getting the same error message when I didn't enter a Subject: line in the DATA portion of the message.

---

### Post by slochewie on 2011-08-05
Here's the latest I have and it's working now.

We use RightScale to manage our Amazon servers. Here's the script I use to successfully configure Amazon SES when we launch a brand new EC2 instance.

```

#!/bin/bash -e
#
#Setups credentials for Amazon SES Perl scripts and copies SES.pm to Perl path.
#
# Test for a reboot,  if this is a reboot just skip this script.
#
if test "$RS_REBOOT" = "true" ; then
  exit 0 # Leave with a smile ...
fi

cd /opt
wget http://aws-catalog-download-files.s3.amazonaws.com/AmazonSES-2011-07-21.zip
unzip AmazonSES-2011-07-21.zip -d amazon-email
touch /opt/amazon-email/aws-credentials

cat > /opt/amazon-email/aws-credentials << EOF
AWSAccessKeyId=$AWS_ACCESS_KEY_ID
AWSSecretKey=$AWS_SECRET_ACCESS_KEY
EOF

chmod 600 /opt/amazon-email/aws-credentials
chown nobody:nogroup /opt/amazon-email/aws-credentials
cp /opt/amazon-email/SES.pm /usr/lib/perl5/
rm AmazonSES-2011-07-21.zip

cp $ATTACH_DIR/Config.pm /etc/perl/CPAN/

cpan -i CPAN
cpan -i LWP::UserAgent

echo "aws-email  unix  -       n       n       -       -       pipe" >> /etc/postfix/master.cf
echo "  flags=R user=nobody argv=/opt/amazon-email/ses-send-email.pl -r -k /opt/amazon-email/aws-credentials -e https://email.us-east-1.amazonaws.com -f \${sender} \${recipient}" >> /etc/postfix/master.cf

echo "sender_canonical_maps = regexp:/etc/postfix/sender_canonical" >> /etc/postfix/main.cf
echo "default_transport = aws-email" >> /etc/postfix/main.cf
touch /etc/postfix/sender_canonical
cat > /etc/postfix/sender_canonical << EOF
/(.*?)@(.*)/ webmaster@$APPLICATION.com
EOF

service postfix restart

```

These are the packages additional Perl packages from the Ubuntu repositories needed:

```

apt-get -y install libdigest-sha-perl liburi-perl libcrypt-ssleay-perl libxml-perl libxml-libxml-perl perl-doc

```

I've attached my /etc/perl/CPAN/Config.pm needed for unattended CPAN installs.

You can test from the command line by performing:
```

mail username@domain.com

```

If you're still in the Amazon SES sandbox mode you'll need to use a verified address.

I was logged in as root so my emails were being sent as [email]root@domain.com[/email] and I was sending to [email]username@domain.com[/email] so both addresses needed to be verified by Amazon SES.

---

