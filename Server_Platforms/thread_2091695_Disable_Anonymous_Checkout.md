---
title: "Disable Anonymous Checkout"
date: 2012-12-05
forum: Server Platforms
---

### Post by MichaelLerch on 2012-12-05
I have been trying to find a way to disable anonymous checkout on Subversion.  I have it set so that in order to commit to the repository, you have to have a username/password.. but it won't ask for it when I do a checkout.

Ubuntu Server 12.04
Apache2
libapache2-svn module
subversion

my dav_svn.conf file looks as follows:

<Location /svn/project/>

DAV svn

AuthType Basic
AuthName "Project"
AuthUserFile /etc/apache2/dav_svn.passwd

</LimitExcept GET PROPFIND OPTIONS REPORT>
Require valid-user
</LimitExcept>


## THE NEXT THREE LINES, I JUST ENABLED
## RESTARTED APACHE
## STILL DOESN'T ASK FOR USERNAME/PASSWORD ON CHECKOUT
## READ BELOW FOR THE LAYOUT OF THE svn_access_control FILE
<IfModule mod_authz_svn.c>
AuthzSVNAccessFile /etc/apache2/svn_access_control
</IfModule>

</Location>


### SVN_ACCESS_CONTROL ###

[/]
* =

### Apparently * is anonymous = [blank] means anonymous can't access the repository.
### What do I do almighty Ubuntu masters.

---

### Post by Vegan on 2012-12-05
check the manual for subversion as that is where all the settings are documented
:guitar::guitar:

---

### Post by MichaelLerch on 2012-12-05
I've read the man page and the online manual. It tells me the same thing I did in my initial post.......

Alright. It appears the fix would be to remove the <LimitExcept> bit and keep Required valid-user. 

<LimitExcept GET ... REPORT>

The GET issues HTTP GET, meaning the user will download. HOWEVER, it allowed for anonymous users to do a checkout. By removing the <LimitExcept> tag altogether you're pretty much saying "Require valid-user" at all times. Which means that at any point such as a checkout, commit, etc a valid-user is required.

My dav_svn.conf file now looks as such:


<Location /svn/project/>

DAV svn  ##This enables the repository.

AuthType Basic #Basic authentication. It's explained in the default dav_svn.conf file.
AuthName "Project" #Gives the project a name
AuthUserFile /etc/apache2/dav_svn.passwd #Is the passwd file that stores users name and password.

Require valid-user #requires that the user be valid in order to checkout, commit, etc. Without the <LimitExcept> it now prevents anonymous checkout!

## THE NEXT THREE LINES, ARE USELESS UNLESS YOU'RE USING svn://server/svn/repo instead of [http://server/svn/repo](http://server/svn/repo)
## so I have commented them out for future use, which may not be at all, but who knows.
#<IfModule mod_authz_svn.c>
#AuthzSVNAccessFile /etc/apache2/svn_access_control
#</IfModule>

</Location>

Now for anyone looking to disable anonymous checkout. You can use my example above to resolve that issue.  Keep in mind however, that using TortoiseSVN will store a cached credential if you've already logged into the repository once before on that system.  So be sure to try [http://server/path/to/repo](http://server/path/to/repo). If it asks for a password, then your issue is fixed and anonymous checkout is disabled. Another way to test it is to download VirtualBox and install Ubuntu 12.04 + RapidSVN - try doing a checkout from your repository. If it asks for a password, it's fixed. If it doesn't, you can feel free to contact me and I'll help you fix it. :)

I hope this helps anyone in the future!

---

