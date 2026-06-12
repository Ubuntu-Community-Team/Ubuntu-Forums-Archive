---
title: "cgi problem with building an html file"
date: 2013-01-25
forum: Server Platforms
---

### Post by IslandBill on 2013-01-25
Hello all,

I'm struggling with a cgi script that builds a temp file and copies over to html.  The script is written in sh:

> 
#!/bin/sh

# Create some temporary files to hold our data:
for i in 1
do
FILE="$$"
FILE2="/tmp/$$.txt"
FILE3="time_$$.html"
# echo $FILE # show file name
> $FILE # create files
done

# Create the html code with the days remaining on the user's remaining 
# account time in decimal format.
# 
echo "Content-Type:text/html \n\n" >> $FILE3
echo "<html>" >> $FILE3
echo "<head>" >> $FILE3
echo "<title>Account Status</title>" >> $FILE3
echo "<body bgcolor=\"0000ff\">" >> $FILE3
echo "<font color='#FF0000' face='fixedsys, lucida console, terminal, vga, monospace' style='line-height: 1; letter-spacing: 0; font-size: 12pt'>" >> $FILE3
echo "echo \"User-Name=$1,User-Password=$2\" | radclient -c '1' -n '3' -r '3' -t '3' -x '127.0.0.1:1812' 'auth' 'secret' 2>&1 | grep Session-Timeout" > $FILE
chmod 755 $FILE
./$FILE | awk '{print "You have "$3/86400" days left to surf."}' > $FILE2 
cat $FILE2 >> $FILE3
echo "</font>" >> $FILE3
echo "</body>" >> $FILE3
echo "</html>" >> $FILE3
# Move the finished html to the document root.
mv $FILE3 /path/to/docroot/
chmod 644 /path/to/docroot/$FILE3
# Command line tests to see if the file wrote correctly. 
# Comment these out to run the script live.
# cat /path/to/docroot/$FILE3
#ls -l $FILE3

# Finally, redirect the user to the page.

echo "<META HTTP-EQUIV=\"REFRESH\" CONTENT=\"2; url=http://www.someurl.com/$FILE3 \">"

Don't laugh, I'm not a coder by trade!  hehe

Anyway, here's the symptom:  if I run this from the command line, everything is great.  I run it as "www-data" from the CL, still great.   I can paste the URL into my browser and all of the information is in there (I get this obviously by doing a long listing and grabbing the newest $FILE3).

 However if I run it in the browser, everything is great EXCEPT the data created by the awk command is left out of the HTML page.  So I end up with a blank blue screen (except that it has the "content-type....blah" on top, an issue for tomorrow).  This occurs whether I try using the "<pre>" tag or not.   And before you ask, I get a similar problem using the perl ansi2html command.

This leads me to ask if this is a permissions issue pertaining to awk?  I dunno....  weird though, at least for a dummy like me.

Any suggestions would be appreciated.  -- And yes, I know I have some housekeeping to do with the code vis-a-vis cleaning up files, etc.  :)

---

### Post by Doug S on 2013-01-25
Did you place your cgi file in /usr/lib/cgi-bin? By default that is the only directory that has the ExecCGI Option set (see /etc/apache2/sites-available/default )

---

### Post by IslandBill on 2013-01-25
Actually, my ScriptAlias does not point to /usr/lib/cgi-bin/.  I changed that during the process.  But it appears I've found the problem.  The script is not gathering the field data from the form.  :lolflag:

---

### Post by IslandBill on 2013-01-25
Follow up for the benefit of future googlers who stumble across this thread:

In hindsight, it would have been better NOT to write this in sh.  It's a pain in the butt when it comes to parsing a form, and apparently (correct me if this statement is outdated) a big potential security risk.

Not being any great shakes at coding in the first place, I wasn't about to take on that job.  So I found an old piece of C code online that was written expressly for capturing form data and passing it to shell scripts.  I compiled it and called it from the above sh script strictly to capture the username and password and store them in variables.  I think this is fine security wise as far as it goes -- the accounts I'm checking exist only for a captive portal that refers to a freeradius server for wifi access.  So even if someone got ahold of them, not the biggest deal in the world.  As you can see, the information is simply passed to radclient for the purpose of checking the remaining time on an account.  Hopefully I'm not being naive :p .

My next step is to rewrite this whole affair in something a little more functional and secure.  Since I'm going to be wanting more information from a mysql database anyway, the obvious choice here is php with perhaps a few other things built into the background as necessary.  

As I said, I'm not a programmer by trade.  I'll hack/borrow/patch-together whatever I need when I need it.  This has been a good learning experience however, and hopefully someone else will benefit from the information.

Cheers!  ):P

---

