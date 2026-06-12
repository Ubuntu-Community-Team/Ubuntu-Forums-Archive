---
title: "FIX: Landscape gives &quot;System error - An unexpected error has occurred.&quot;"
date: 2016-04-14
forum: Ubuntu Cloud and Juju
---

### Post by twin-turbo on 2016-04-14
My Landscape error was giving errors on when selecting multiple machines.

System error
An unexpected error has occurred. This event has been logged.
We apologize for the inconvenience. Please contact Canonical Support for >further assistance.
OOPS ID: 3490DFA8 


on investigation with a nod from this thread...

[http://askubuntu.com/questions/651883/landscape-script-error](http://askubuntu.com/questions/651883/landscape-script-error)

I tried a number of times to update the serve URL with o JOY.

I delved deeper, and found that during my install I must have specified the server name in Capitals , this had carried through to the apache virtal host config.

de-capitalising all references in the file solved my errors.

edit references in

#nano /etc/apache2/sites-enabled/your-lusus-server.conf

restart apache

#apache2ctl restart


Hope that helps someone else.

TT

---

