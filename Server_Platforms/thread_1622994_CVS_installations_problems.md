---
title: "CVS installations problems"
date: 2010-11-16
forum: Server Platforms
---

### Post by fellow_cons on 2010-11-16
Hello,

i dont get the CVS  to run:

CVS dir looks like this..

/var/lib/cvsd$
bin cvsrepo dev etc lib lib64 root tmp usr var

the repositroy is at cvsrepo
/var/lib/cvsd/cvsrepo

CVSROOT

/var/lib/cvsd/cvsrepo/CVSROOT

checkoutlist cvswrappers modules postadmin,v postwatch,v taginfo,v
checkoutlist,v cvswrappers,v modules,v postproxy preproxy val-tags
commitinfo Emptydir notify postproxy,v preproxy,v verifymsg
commitinfo,v history notify,v posttag rcsinfo verifymsg,v
config loginfo passwd posttag,v rcsinfo,v
config,v loginfo,v postadmin postwatch taginfo


/etc/xinetd.d/cvspserver 

service cvspserver
{
port = 2401
socket_type = stream
protocol = tcp
#user = cvs
#group = cvsgroup
user = cvsd
group = cvsd
wait = no
type = UNLISTED
server = /usr/bin/cvs
server_args = -f --allow-root /var/lib/cvsd/cvsrepo pserver
disable = no
}


sudo cvs -d :pserver:xxx@localhost:/cvsrepo login
Logging in to :pserver:xxxx@localhost:2401/cvsrepo
CVS password: 
cvs [login aborted]: unrecognized auth response from localhost: cvs [pserver aborted]: /cvsrepo: no such repository

Everytime i get this error above..

Service is running at port 2401, cause i can connect via telnet at this port.
Somebody has an idea ??


regards
Steve

---

