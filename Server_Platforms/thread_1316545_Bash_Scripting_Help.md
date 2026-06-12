---
title: "Bash Scripting Help"
date: 2009-11-06
forum: Server Platforms
---

### Post by krauser530 on 2009-11-06
So I've written a little bash script to parse incoming email and I'm having trouble replying. There are certain email addresses I receive that are in the format **username#email.host@another.host** and I would like to reply to **username@email.host** and leave off the end. This is what I've come up with for that:

cut -d\< -f2 $file | cut -d\> -f1 | cut -d@ -f1 | head -1 > /home/dk/dev/temp.txt
cut -d\# -f1 /home/dk/dev/temp.txt > /home/dk/dev/email.txt
echo -n '@' >> /home/dk/dev/email.txt
cut -d\# -f2 /home/dk/dev/temp.txt >> /home/dk/dev/email.txt
	    
email=$(tr -d '\n' < /home/dk/dev/email.txt)
	    
mutt -s "Subject" -a /home/dk/dev/thumb.jpg -a /home/dk/dev/full.jpg "$email" < /home/dk/dev/body.txt

The script seems to work up until the last line. If i just echo the email variable, it displays the right information, but mutt sends the email with no outgoing address. I get a return email that says malformed email address as the field is empty. What is wrong with my syntax on the last line?

---

### Post by krauser530 on 2009-11-06
Never mind figured it out. The script was working, the email server wasn't.

---

