---
title: "cgi-script problem"
date: 2008-01-12
forum: Server Platforms
---

### Post by davidc502 on 2008-01-12
All,

I've installed Apache on Ubuntu and it works great. I wrote a little cgi-script in shell that captures fields from a form and writes this to a text file on the hard drive. The fields captured from the web page are URL and Email address. The problem I'm having is that the @ in email addresses and ://  in URLs come over as hexadecimal. 

Example testing.com and [email]test@testing.com[/email] are written like this.

url=http%3A%2F%2Ftesting.com&email=test%40testing.com

How can I keep characters such as @ and :// from coming over as hexadecimal?

Thanks,

David

---

### Post by davidc502 on 2008-01-12
Problem solved. I used the 'sed' content filter to replace the hex with the appropriate value.

I omitted the html in this shell script, but kept the relevant information.

cat >> /home/david/Desktop/log/logfile.txt
sed -i 's/%40/\@/g' /home/david/Desktop/log/logfile.txt
sleep 1
sed -i 's/%3A/\:/g' /home/david/Desktop/log/logfile.txt
sleep 1
sed -i 's/%2F/\//g' /home/david/Desktop/og/logfile.txt
sleep 1
sed -i 's/&/\ /g' /home/david/Desktop/log/logfile.txt

echo Done and redirecting.....

---

### Post by davidc502 on 2008-01-12
I also created a separator page. I cat into the page, copy the contents I want and the next entry goes on the next line. This keeps the lines from running one after the other.

Anyhow. Case Closed.

---

