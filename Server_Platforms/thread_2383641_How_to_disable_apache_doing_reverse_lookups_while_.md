---
title: "How to disable apache doing reverse lookups while using a .htaccess file"
date: 2018-01-27
forum: Server Platforms
---

### Post by Doug S on 2018-01-27
On my web site I have a directory with simple restricted access using an .htaccess file. The apache server does reverse lookups for any client that is accessing those web pages. It never does reverse loookups for any access to normal pages. I do not want apache doing reverse loookups, but haven't been able to figure how to disable them.

HostnameLookups is set to Off in the apache.conf file:
```
#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

```

I found a couple of references that say to not have comments at the end of a line in the .htaccess file,  which I don't.
I also don't have any deny via fqdn in the file. Here is the file:
```
Allow from valid-user
Authtype basic
AuthName "Registered users only"
AuthUserFile /home/doug/.htkes
Require valid-user

```Does anyone know how to disable the reverse lookups?

EDIT: If I eliminate the .htaccess file and do it via /etc/apache2/sites-available/000-default.conf instead, the reverse lookup issue persists.

---

### Post by Doug S on 2018-01-28
I finally found [this]("https://serverfault.com/questions/100225/apache-httpd-wont-stop-doing-reverse-dns-requests-for-clients-ips").

> It seems the standard Ubuntu Apache httpd install comes with a LogFormat that starts with %h and that does a client IP's RDNS lookup. Why oh why?? Replacing it with %a (remote IP address, see custom log formats) reduces this problem by ca. 90%. Some remain...So, I did this:
```
doug@DOUG-64:~/config/etc/apache2$ [COLOR="#FF0000"]diff -u apache2.conf.003 apache2.conf[/COLOR]
--- apache2.conf.003    2018-01-28 08:59:25.356021844 -0800
+++ apache2.conf        2018-01-28 09:01:34.909828618 -0800
@@ -1,3 +1,7 @@
+# 2018.01.28 Smythies:
+#      Try changing logfile format from %h to %a.
+#      in an attempt to eliminate reverse DNS lookups
+#
 # 2016.02.04 Smythies:
 #      apache no longer supplies the imagemap module by default,
 #      so take out the AddHandler stuff.
@@ -215,9 +219,9 @@
 # Note that the use of %{X-Forwarded-For}i instead of %h is not recommended.
 # Use mod_remoteip instead.
 #
-LogFormat "%v:%p [COLOR="#FF0000"]%h[/COLOR] %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
-LogFormat "[COLOR="#FF0000"]%h[/COLOR] %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
-LogFormat "[COLOR="#FF0000"]%h[/COLOR] %l %u %t \"%r\" %>s %O" common
+LogFormat "%v:%p [COLOR="#FF0000"]%a[/COLOR] %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
+LogFormat "[COLOR="#FF0000"]%a[/COLOR] %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
+LogFormat "[COLOR="#FF0000"]%a[/COLOR] %l %u %t \"%r\" %>s %O" common
 LogFormat "%{Referer}i -> %U" referer
 LogFormat "%{User-agent}i" agent

```And the issue seems to be fixed.

EDIT: One might wonder if it is just the logging of the reverse lookup name that changed to IP, but that the actual reverse lookup still occurs. I used tcpdump and verified that there are no actual reverse lookups.

---

