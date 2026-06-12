---
title: "Apache + Modsecurity Issues with Safari 6 Update"
date: 2013-01-23
forum: Server Platforms
---

### Post by kaledragule on 2013-01-23
Hello,

We are having an issue ever since Apple release the update for Safari 6 where client's using the browser are filling up our Apache logs with entries like the following in the SSL error log for the webapp:

[20/Jan/2013:23:55:21 -0500] "GET /WebAdvisorST/WebAdvisor?TYPE=M&PID=CORE-WBMAIN&TOKENIDX=4861441791 HTTP/1.1" 200 320 "https://mycollege2.cpcc.edu/WebAdvisorST/WebAdvisor?TYPE=M&PID=CORE-WBMAIN&TOKENIDX=4861441791" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5) AppleWebKit/536.26.17 (KHTML, like Gecko) Version/6.0.2 Safari/536.26.17"

These entries occur multiple times a second for 10 minute spans of time and then repeat. At first we though we had DDoS attack and we began blacklisting IP addresses on the firewall. Then we found that the entries started when Apple release Safari 6. We had two options at the time as we were under time constraints. One was to put a proxy in place and deny all traffic from Safari, and the other was to sanitize the logs in order to free up storage space via cron.

We have now updated our servers, converted from Debian to Ubuntu(12.04.1 LTS), upgraded Apache(2.2.22) and are using modsecurity 2.6.3. Now we are getting entries like the following in the mod_security log causing it to fill up 12GB+ of space:

Message: Warning. Match of "eq 1" against "&ARGS:CSRF_TOKEN" required. [file "/etc/apache2/modsecurity_rules/modsecurity_crs_43_csrf_protection.conf"] [line "31"] [id "981143"] [msg "CSRF Attack Detected - Missing CSRF Token."]

From what I can tell, the modsecurity log entries correspond to the apache entries caused by the Safari browser. The CSRF rule is an optional rule in modsecurity so I had considered disabling it to resolve the log issues, but I was hoping that I could find a fix for the root cause, Safari.

There has to be other people out there who have experienced similar issues. I'm hoping that there is some patch I'm missing, or some workaround that I need to put in place. Any ideas, or do you need any more detailed info to help troubleshoot?

TIA

---

### Post by kaledragule on 2013-02-06
Found the solution on another site. Looks like it's an issue with the Top Sites piece in Safari and the tokens used in the Tomcat webapp.

> Well, what we found out is that the Top Sites feature is trying to go to the URL that is being saved, which contains a TOKENIDX variable that is invalid, fails to reach the site because of a redirect saying 'invalid session' (or similar) and just tries and tries and tries and tries. It also looks like it's something that changed in Safari 6 and persists in 6.0.1

Here's a solution to this issue. Place the following before function initWindow():
```
if(window.navigator && window.navigator.loadPurpose === "preview"){
    window.location.href = "http://sample.edu/common/images/logo.jpg";
}
```
Of course, you'd want to switch out the location with something of your own :) The "loadPurpose === "preview"" item was snagged from iCloud's web site which prevents Top Sites from rendering a snapshot of the site.


---

