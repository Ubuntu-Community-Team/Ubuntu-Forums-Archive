---
title: "Trying to specific lines of a log file to another log file"
date: 2009-07-09
forum: Server Platforms
---

### Post by buee on 2009-07-09
Hello,

I have a number of websites on my virtual machine and the access-logs are getting considerably long.  I've tried to figure out how to block access based on IP address to the login page, but it's Drupal and appears to be quite difficult.  I wonder if it would be easier to put a command in cron that would output the lines from the log file that contain that specific URL to a different log file call "Naughty-access.log".  If that's not clear, perhaps showing you the command that I've already tried:

```
cat domain1-access.log | grep *www.domain1.com/user* > Naughty-access.log
```

Basically find the string "*www.domain1.com/user*" in domain1-access.log file and output all _lines_ containing that string to the file domain1-access.log

Is that possible?

---

### Post by slugmax on 2009-07-09
You can do that like this:

```

grep 'www.domain1.com/user' domain1-access.log > naughty-access.log

```

The 'cat' is redundant, since you specify the input file with grep anyway, and the asterisks are not needed, since grep matches complete substrings one line at a time.

Doug

---

### Post by buee on 2009-07-09
> **slugmax said:**
> You can do that like this:

```

grep 'www.domain1.com/user' domain1-access.log > naughty-access.log

```

The 'cat' is redundant, since you specify the input file with grep anyway, and the asterisks are not needed, since grep matches complete substrings one line at a time.

Doug

Awesome, thanks!

One last question.  Will that keep appending the file it I put that in cron?  Or will it keep duplicating Naughty-access.log?

---

### Post by Wim Sturkenboom on 2009-07-09
Sorry, read the question wrong.

---

### Post by slugmax on 2009-07-09
> **buee said:**
> Awesome, thanks!

One last question.  Will that keep appending the file it I put that in cron?  Or will it keep duplicating Naughty-access.log?

No problem. 

It will overwrite naughty-access.log each time you run it. If you want to append to that file, use '>> naughty-access.log'.

---

### Post by buee on 2009-07-10
Ok, riddle me this.  When looking at the file, it logs each time I log in and shows my internal or external IP address, but neither ever change.  Is there a way I can filter those IP addresses out?

Like:
```

grep 'www.domain1.com/user' && !192.168.1.1 && !93.24.49.39 domain1-access.log >> naughty-access.log

```

Or possibly output to the file, then open the file again with the script and delete those lines maybe?

---

### Post by slugmax on 2009-07-11
Sure:

```

grep 'www.domain1.com/user' domain1-access.log | grep -v '192\.168\.1\.1' | grep -v '93\.24\.49\.39' >> naughty-access.log

```

The -v option to grep says to match all the lines but those matching the filter expression. The backslash prevents the period from being interpreted as a regular expression meta-character meaning 'match any single character', so it just matches a literal period, which is what you want.

Doug

---

### Post by buee on 2009-07-14
> **slugmax said:**
> Sure:

```

grep 'www.domain1.com/user' domain1-access.log | grep -v '192\.168\.1\.1' | grep -v '93\.24\.49\.39' >> naughty-access.log

```

The -v option to grep says to match all the lines but those matching the filter expression. The backslash prevents the period from being interpreted as a regular expression meta-character meaning 'match any single character', so it just matches a literal period, which is what you want.

Doug

I vote you change your name to Obi Wan.

Still not done with this script.  I noticed that all of my log files are getting quite large.  Is there any way to delete lines older than **x** days/weeks/months?  Otherwise, they'll fill up the drive.

Also, on the error log.  I've managed to figure out how to output the portions that contain the IP address, but I'll like to trim it down to JUST the IP address so I can just copy and paste them over to the .htaccess file.  Currently, it's outputting the whole line.

---

### Post by Wim Sturkenboom on 2009-07-15
> **buee said:**
> I noticed that all of my log files are getting quite large.  Is there any way to delete lines older than **x** days/weeks/months?  Otherwise, they'll fill up the drive.
Read up on logrotate. You can start with [man logrotate](http://linuxcommand.org/man_pages/logrotate8.html) ;)

---

### Post by slugmax on 2009-07-15
> **buee said:**
> I vote you change your name to Obi Wan.

*grin*

> Also, on the error log.  I've managed to figure out how to output the portions that contain the IP address, but I'll like to trim it down to JUST the IP address so I can just copy and paste them over to the .htaccess file.  Currently, it's outputting the whole line.

You'll have to try harder than that :-). I like to use Perl for this:

```

grep 'www.domain1.com/user' domain1-access.log | grep -v '192\.168\.1\.1' | grep -v '93\.24\.49\.39' | perl -nle 'print $1 if /(\d+\.\d+\.\d+\.\d+)/' >> naughty-access.log 

```

This will only grab the first IP in each line, so if there are more than that, you'll need to post a sample of the log file. If it's just a standard Apache access log, you're OK.

'perldoc perlrun' if you are curious about the Perl syntax.

---

