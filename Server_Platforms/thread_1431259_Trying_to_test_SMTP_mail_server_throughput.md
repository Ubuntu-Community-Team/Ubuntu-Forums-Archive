---
title: "Trying to test SMTP mail server throughput"
date: 2010-03-16
forum: Server Platforms
---

### Post by lcsfsr1 on 2010-03-16
Hello,
I am trying to find out how to test SMTP mail server throughput.

I found a program that sounds like it might work.  It is called Postal. It is located here:
[http://manpages.ubuntu.com/manpages/jaunty/man8/postal.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/postal.8.html)

I have not been able to figure out how to use it though.  The very few instructions that I have found are very vague.

Could someone please explain how to use this program??

If there is another program that would accomplish this better then please tell me and show me how to use that program.

Thanks,

Bobby Howerton

---

### Post by KB1JWQ on 2010-03-16
A lot's going to depend on the particular messages.  I can email you an mp3 file a lot more slowly than I can send you 500 messages saying simply "Test."

Let's take a step back-- what's your concern, in real-world terms?  How is the box going to be used (sending only, receiving only, is it going to be doing any POP/IMAP/database work, what's your daily message volume target, etc)?

---

### Post by lcsfsr1 on 2010-03-17
Ok,
It is going to be sending only...there will be "no" receiving email on this server.

The program that is in place to automate this process is (built in house...custom made by our programmers) so that when the program runs we are able to select the client, then select the type of promotion or type of E-Blast that the client has paid for, we then attach an html file as the body of the e-mail then click launch.

After you click launch, the program goes into the Microsoft SQL database, locates the clients customer database (the database that contains the e-mail addresses that the client wants to use).  It then loads those addresses and sends the e-mail/e-blast to the clients customers.

As an example at lunch time 1 of our clients want a "Whats for Lunch" E-Blast sent out to approx 2000 people to let them know...Whats for Lunch today.

We just need to make sure that this is going out as quickly as possible...It would not be good if the clients customers received this e-mail after lunch was over.

This is why I am trying to determine the throughput of the SMTP server.

Thanks again for the help,

Bobby

---

### Post by KB1JWQ on 2010-03-17
On any modern email system, 2000 messages should go out in under 2 minutes.  If you're sending to remote sites, greylisting and tempfails become much more of a concern.  Email is USUALLY instant, but that's by no means guaranteed.

As an example, I had a server start throwing errors from cron.hourly.  Because I hadn't configured my mail subsystem properly on that box, the messages languished in the queue without hitting expiry, or attempting to move on to the next-hop destination.  By the time I noticed this, I had 2700 emails on it.  After fixing the problem and bouncing the mail system, those 2700 messages were gone in about 45 seconds.  This wasn't beefy hardware, this was a VM living on top of a cheap $700 box.

Long story short, any modern mail system should be able to meet or exceed the example you've given me without tweaking. :-)

---

### Post by lcsfsr1 on 2010-03-17
Ok thanks,
Now given the fact that we are getting more and more of a "needed" type response (meaning that people are wanting and willing to pay for this type of service) it is thought that we may very well be up to sending 20,000 to 30,000 emails per client by this summer.


[LIST]
[*]How can I tweak this server so that we can handle that type of load with no problem...meaning that it will process 30,000 emails almost instantly, if not instantly then very quickly (like within an hour or two)???
[/LIST]
We have a lot of clients and we definately do not need to have any kind of slow down.  I mean even if you say 10 clients who have an approx 10,000 emails (which I am sure will be a low number) that will be sent out.....it seems like this will be a large load on the server.


[LIST]
[*]Do you know how to use the Ubuntu program Postal to test the SMTP throughput???
[/LIST]

[LIST]
[*]Do you know of any way to monitor and check this on a regular basis???
[/LIST]
Thanks,

Bobby

---

### Post by KB1JWQ on 2010-03-17
Initially one server will work, but as your load grows you may want to look into running multiple mailservers.

I'd monitor it on an ongoing basis using Nagios, specifically the check_mailq plugin to ensure that the queue remains under a predefined threshold.

As far as using postal goes, it's pretty intuitive; man postal if you get stuck. :-)

---

### Post by lcsfsr1 on 2010-03-17
OK,
I will check on the Nagios check_mailq plugin.

As for Postal (the help file is very vague), I think I can figure it out, but the only questions that I have is:

Considering the syntax: postal _sender-file_ _smtp-server_ _user-list-filename_
       The  **smtp-server** parameter specifies the IP address or name of the mail
       server that the mail is to be sent to.  Mail sent by  **Postal**  will  not
       use  MX  records, this is to allow testing outbound relays etc.  If you
       want to specify a port other than port 25 then enclose the host address
       in square brackets and have the port address immidiately following.  If
       you want a DNS lookup for every  connection  (for  testing  round-robin
       DNS)  then  immediately  preceed the host address with a ’+’ character.
       To specify multiple servers  for  round-robin  use  then  seperate  the
       addresses  with  commas.  Note that **localhost** is used for connecting to
       the same machine.

       The **user-list-filename** is the name of a file which contains a  list  of
       user’s email addresses.  This can be just user-names or fully qualified
       email addresses.  Whatever you specify will be sent exactly in the SMTP
       protocol  so  make sure you do whatever is appropriate.  If unsure then
       use fully qualified addresses (IE [EMAIL="user@example.com"]user@example.com[/EMAIL]).

       The **sender-file** contains a list of users that  will  be  in  the  From:
       field and envelope sender of the messages.  If it is not specified then
       the user-list-filename will be used for the sender list.

[FONT=Verdana][SIZE=2][COLOR=Red]Where are these three files located at??? [/COLOR] It says that they contain stuff like a list of e-mail addresses or a list of users.  

If I need to populate these files....

[COLOR=Red]How do I do that???[/COLOR]  I do not know where they are located.  [COLOR=Red]

How do I populate these list???[/COLOR]
[COLOR=Red]
Is there a way to populate these list??? 

What data / information goes into these files???[/COLOR]



Also, [COLOR=Red]what do I use as the smtp-server???[/COLOR] 

[COLOR=Red]Do I use The IP Address or the mail server hostname, etc???

[COLOR=Black]Thanks,

Bobby
[/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by KB1JWQ on 2010-03-17
The two files can live anywhere you want them to, just reference them by absolute or relative path; it really doesn't matter.  Create new files, drop the data they want (a list of email addresses, one per line is standard).  

The SMTP server is either the IP or hostname of the server you're looking to test.

---

### Post by lcsfsr1 on 2010-03-18
Ok,
I created the folders as you have said (both in the same directory as postfix and the same directory as postal.

Now, for testing purposes, in the sender-file I have my e-mail address.
In the user-list-filename I have a a couple of more valid e-mail addresses.

As I said earlier my ip address is 172.nnn.NNN.nnn.  This ip address is in the DMZ.

I have tried to execute postal in a couple of different ways (even using the path to the file)...it does not seem to work.  What am I doing wrong

What I have typed each time is in **BOLD**


[LIST]
[*]I created the 2 files in the /etc/postfix directory (where postfix is installed), then ran these commands...nothing worked.
[/LIST]

Bobby@abc-eblast:/etc/postfix$ **postal -a sender-file 172.nnn.NNN.nnn user-list-filename**
Usage: postal [-m maximum-message-size] [-M minimum-message-size] [-t threads]
              [-c messages-per-connection] [-r messages-per-minute] [-a]
              [-b [no]netscape] [-p port] [-[z|Z] debug-file]
              [-s ssl-percentage]
              [-l local-address] [-f sender-file]
              smtp-server user-list-filename

Postal Version: 0.70
Bobby@abc-eblast:/etc/postfix$ **postal -a /etc/postfix/sender-file 172.nnn.NNN.nnn /etc/postfix/user-list-filename**
Usage: postal [-m maximum-message-size] [-M minimum-message-size] [-t threads]
              [-c messages-per-connection] [-r messages-per-minute] [-a]
              [-b [no]netscape] [-p port] [-[z|Z] debug-file]
              [-s ssl-percentage]
              [-l local-address] [-f sender-file]
              smtp-server user-list-filename

Postal Version: 0.70
Bobby@abc-eblast:/etc/postfix$ **postal -m 10 -t 20 -c 20 -a /etc/postfix/sender-file 172.nnn.NNN.nnn /etc/postfix/user-list-filename**
Usage: postal [-m maximum-message-size] [-M minimum-message-size] [-t threads]
              [-c messages-per-connection] [-r messages-per-minute] [-a]
              [-b [no]netscape] [-p port] [-[z|Z] debug-file]
              [-s ssl-percentage]
              [-l local-address] [-f sender-file]
              smtp-server user-list-filename


[LIST]
[*]I created the 2 files in the /usr/sbin directory (where postal is installed), then ran these commands...nothing worked.
[/LIST]

Bobby@abc-eblast:/usr/sbin$ **postal -a sender-file 172.nnn.NNN.nnn user-list-filename**
Usage: postal [-m maximum-message-size] [-M minimum-message-size] [-t threads]
              [-c messages-per-connection] [-r messages-per-minute] [-a]
              [-b [no]netscape] [-p port] [-[z|Z] debug-file]
              [-s ssl-percentage]
              [-l local-address] [-f sender-file]
              smtp-server user-list-filename

Postal Version: 0.70
Bobby@abc-eblast:/usr/sbin$ **postal -m 10 -t 20 -c 20 -a /usr/sbin/sender-file 172.nnn.NNN.nnn /usr/sbin/user-list-filename**     
Usage: postal [-m maximum-message-size] [-M minimum-message-size] [-t threads]
              [-c messages-per-connection] [-r messages-per-minute] [-a]
              [-b [no]netscape] [-p port] [-[z|Z] debug-file]
              [-s ssl-percentage]
              [-l local-address] [-f sender-file]
              smtp-server user-list-filename

Thank you for your help!!!

Bobby

---

### Post by jrssystemsnet on 2010-03-18
Why are you issuing ```
postal **-a sender-file** 172.nnn.NNN.nnn user-list-filename
``` at all?

Closely read the error message Postal gave you, it tells you what it needs:

> Usage: postal [-m maximum-message-size] [-M minimum-message-size] [-t threads]
[-c messages-per-connection] [-r messages-per-minute] [-a]
[-b [no]netscape] [-p port] [-[z|Z] debug-file]
[-s ssl-percentage]
[-l local-address] **[-f sender-file]**
smtp-server user-list-filename

So, ```
postal -f /path/to/sender-file ip.address.of.smtp.server /path/to/user-list
``` is the correct syntax.

I have to warn you though, you're spinning your wheels here.  Your real problem isn't going to be raw throughput of your server, your real problem is going to be the vast majority of the internet absolutely refusing your traffic after a couple of times you send out an "e-blast".  Without A LOT of specialized knowledge about bulk mail distribution, you're going to end up on every one of the private blacklists (Time Warner, AT&T, Comcast, MSN, etc) immediately, and most likely you'll end up on the public ones (SpamCop, SORBS, Spamhaus) almost as quickly.  Blacklists aside, you're not going to get the kind of performance Postal would lead you to expect, because the mailservers on the other end are going to tarpit you, greylist you, and otherwise generally discourage what you're trying to do.

If you really want to have a snowball's chance in Miami of making your venture successful, forget about Postal and instead spend the time and effort in learning how to get whitelisted as a legitimate bulk mail provider with all the big carriers, and how to CLEAN CLEAN CLEAN your userlist.  Otherwise you're just going to waste EVERYBODY's time, effort, and money - your clients', your own, and that of the target mailservers that don't want to talk to you.

---

