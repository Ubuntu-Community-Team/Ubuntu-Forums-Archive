---
title: "How are they accessing the login page? WP/LAMP (ngnix?!)"
date: 2014-08-13
forum: Security
---

### Post by mastablasta on 2014-08-13
actually it seems it's ngnix not apache anymore...not sure if it matters in this case.

i am having attempts at someone trying to guess the admin username on wordpress (probably to conduct a bruteforce attempt later on or do some guessing). While i could block them i think it would be better if they received 404 instead when whey they try to access the page.

this is my rule (I removed the IP):

```
<Files wp-login.php>
order deny,allow
allow from homeIP
allow from workIP
allow from broIP
deny from all
</Files>
```


now this when I tried to access this file/link from unauthorised IP gave me a 404 message.

now i am getting russian IP trying to login (2 days ago they attempted once with admin, yesterday they tried the page name as user name). so, why is this rule not working?
should I make the whole server not accessible to this IP?

---

### Post by JetStorm on 2014-08-13
You haven't specified the location of this rule.  If it was added in a .htaccess file and later apache was replaced with nginx it won't work because nginx doesn't use those .htaccess files.

---

### Post by mastablasta on 2014-08-13
right, that makes sense. I need to first confirm If it is apache or nginx. though why would WP plugins then create htaccess files (e.g. sucuri)? and i have all apache stuff in cpanel, htaccess fiels all over the place but the whois is showing nginx. edit: and the redirect rules in htaccess seem to be working. could it be the site is using both servers and reporting nginx?

is the location not everything below .htaccess file?

---

### Post by JetStorm on 2014-08-13
> **mastablasta said:**
> is the location not everything below .htaccess file?

What I meant was that the rule could be located inside the .htaccess file, inside the apache configuration files or inside the nginx config file if that is what the server is running.

---

### Post by mastablasta on 2014-08-13
the rule in in .htaccess. 

although externally it shows as if the server is running nginx the htaccess fiels i have seem to be working. so it's either a combo or actualyl Apache. I need to check this with host. i didnt' receive any info that tehy plan to switch.

also cpanel is full of Apache stuff.

---

