---
title: "Perl cgi"
date: 2006-07-19
forum: Server Platforms
---

### Post by Jates on 2006-07-19
Hi everyone.
I am trying to run perl scripts in a virtualhost of apache 2.
the script I am trying to run is inside cgi-bin.
I get a 500 internal server error.
I did chmod 755  to cgi-bin and to the script I am trying runing but that doesn' t works.

I tried with the script 
#!/usr/local/bin/perl
print "Content-type: text/html\n\n";
print "Prueba\n";

But the other script sends me 500 internal server error.
And I know that script is ok, because that script has been runed many times in other machines.

Any idea to solve this problem?

     Advancing thanks.

---

### Post by Johnsie on 2006-07-23
I've had the same problem alot when I copied my scripts over to a new server.... Try using an ftp client and uploading it to your server as ASCII and see if that m makes any difference.

That worked for me... It seems that somewhere along the line they had been copied badly. 

I miss programming in perl/cgi :.-(

---

### Post by mdecler2 on 2006-07-25
What was in the Apache error log?

---

