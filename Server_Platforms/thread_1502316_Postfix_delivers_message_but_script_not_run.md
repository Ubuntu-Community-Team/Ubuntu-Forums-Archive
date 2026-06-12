---
title: "Postfix delivers message but script not run"
date: 2010-06-05
forum: Server Platforms
---

### Post by rstackhouse on 2010-06-05
Hi, I'm trying to get messages sent to an alias to invoke a ruby script.

Looking at the postfix log the message is being delivered, but I believe the script isn't being run with sufficient permissions.

> Jun  3 18:31:21 hostname postfix/local[12968]: 340B911A3B4: to=<email@domain.com>, relay=local, delay=0.24, delays=0.2/0.01/0/0.03, dsn=2.0.0, status=sent (delivered to command: /var/mailscripts/script)

The script is really simple:

```
#!/usr/bin/env ruby1.9

text = ARGV[0]

puts `echo "#{text}" >> /var/mailscripts/myfile`

```

It _should_ just write the message to myfile. I'm not exactly sure what user/group postfix runs under, and I believe this is the heart of my problem.

---

### Post by scorp123 on 2010-06-05
So ... we're basically talking about a mail-bot, right? I wrote one too ... it's a relatively simple and stupid shell script that gets auto-executed every 15 minutes, connects to a Google account and then downloads and executes the commands I sent to it.

If you want I'll post it here ... ?

---

### Post by rstackhouse on 2010-06-06
No, I'm using the alias file to invoke a script. Like this:

> alias: |/var/mailscripts/script

Thanks for responding though.

---

### Post by scorp123 on 2010-06-06
> **rstackhouse said:**
> No, I'm using the alias file to invoke a script.  Hmmm ... I don't get it. What's the purpose of this?

My mail-bot will download a mail from a specific account (can be configured), do some basic checks and then execute whatever command it was sent, and then send the results back to a specific recipient account (can be configured too). Basically everything that doesn't require keyboard input will work tip top. I can trigger downloads via wget and gcc compile jobs just by writing an e-mail. So yes, it's kind of a backdoor back into the system. I needed that because that particular place where it's installed is behind a super-flaky and unstable router, and sometimes all OpenVPN processes are hanging. Very often this "backdoor" is the only way back in ... the only other alternative would be to get into a car and drive 100 km to the server room.

Are you trying to implement something like this (I suppose my flaky router isn't the only one on this planet ... ?) or am I totally misunderstanding your intentions and goals?

---

### Post by sydesy on 2010-06-06
> **scorp123 said:**
> Hmmm ... I don't get it. What's the purpose of this?


Probably to have it real time as opposed of having to spool a mailbox from time to time. That's how the mailing list managers handles the msg for instance.

What are the permission of ?

/var/mailscripts/myfile

(or /var/mailscripts)

If you want to write some bot or something, have a look at lamsonproject.org might provide you a good framework and take care of quite a few tedious stuff.

---

### Post by rstackhouse on 2010-06-06
> **scorp123 said:**
> Hmmm ... I don't get it. What's the purpose of this?

sydesy hit it right on the nose. I want to take messages delivered to a particular email alias and relay them to an HTTP based messaging service in near real time.

A fellow seemed to have similar woes over [here]("http://blog.tplus1.com/index.php/2008/05/21/frustration-with-postfix-and-sending-email-to-a-script/"). 

From what he's saying, it looks like you have to have a user in Ubuntu that matches the name of the email alias that is sending the mail message to a script.

I had just assumed that the script would be invoked under either root or the account running postfix.

I am still a bit of a newb, especially when it comes to permissions.

---

### Post by scorp123 on 2010-06-06
> **rstackhouse said:**
> sydesy hit it right on the nose. I want to take messages delivered to a particular email alias and relay them to an HTTP based messaging service in near real time.

A fellow seemed to have similar woes over [here]("http://blog.tplus1.com/index.php/2008/05/21/frustration-with-postfix-and-sending-email-to-a-script/"). 

Ah OK ... I get it now :)

---

### Post by rstackhouse on 2010-06-06
I changed the script to 
```
#!/usr/bin/env ruby1.9
require 'etc'

text = "ARGV.length #{ARGV.length} login #{Etc.getlogin}"

puts `echo "#{text}" >> /var/mailscripts/myfile`

```

and chmoded /var/mailscripts to 777. When I do this, it shows me the script is being invoked by my user with the same name as my alias, but ARGV.length is 0. IOW, it looks like the message contents aren't being passed to the script.

the user owns the script directory and the script itself, but if I chmod both back to 755, the file won't get created, but it will get appended to if it is already there.

---

### Post by rstackhouse on 2010-06-07
I changed the script and now the message gets written to file, but there is still the permissions issue

```
#!/usr/bin/env ruby1.9
require 'fcntl'

#http://blog.footle.org/2008/08/21/checking-for-stdin-inruby/

text = ""

if STDIN.fcntl(Fcntl::F_GETFL, 0) == 0 #check stdin for message
        text = "got something: #{STDIN.read}"
elsif ARGV.length > 0 #check command line arguments
        text = "got something:  #{ARGV[0]}"
else
        text = "no message found"
end

File.open('/path/to/myfile', 'w') {|f| f.write(text) }

```

---

