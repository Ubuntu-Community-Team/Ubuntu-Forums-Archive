---
title: "Modsecurity preventing me from browsing from localhost"
date: 2012-10-27
forum: Security
---

### Post by JimJoe on 2012-10-27
Does anybody have a suggestion here?

my appache log spits out the following. 
[Sat Oct 27 20:16:39 2012] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected 'up' (T_STRING) in /var/www/wiki/LocalSettings.php on line 136
[Sat Oct 27 20:16:39 2012] [error] [client 127.0.0.1] ModSecurity: Access denied with code 403 (phase 4). Pattern match "^5\\\\d{2}$" at RESPONSE_STATUS. [file "/etc/modsecurity/activated_rules/modsecurity_crs_50_outbound.conf"] [line "53"] [id "970901"] [rev "2.2.5"] [msg "The application is not available"] [severity "ERROR"] [tag "WASCTC/WASC-13"] [tag "OWASP_TOP_10/A6"] [tag "PCI/6.5.6"] [hostname "localhost"] [uri "/wiki/index.php"] [unique_id "XXXXXXXXXXXXXXXXXX"]
[Sat Oct 27 20:16:39 2012] [error] [client 127.0.0.1] ModSecurity: Warning. Operator GE matched 4 at TX:outbound_anomaly_score. [file "/etc/modsecurity/activated_rules/modsecurity_crs_60_correlation.conf"] [line "40"] [id "981205"] [msg "Outbound Anomaly Score Exceeded (score 4): The application is not available"] [hostname "localhost"] [uri "/wiki/index.php"] [unique_id "XXXXXXXXXXXXXXXXXX"]

do i need to edit modsecurity_crs_50_outbound.conf @ line 53 somehow?
or
modsecurity_crs_60_correlation.conf @ line 40?

---

### Post by JimJoe on 2012-10-27
What I have just tried without any luck:
Created file in \etc\modsecurity\base_rules
called it modsecurity_crs_15_customrules.conf
then added the following
<Location "/wiki/index.php">
SecRemoveRuleById 970901
SecRemoveRuleById 981205
</Location>

i then restarted apache and received the same errors when trying to brows from localhost

guess i'm not sure about the syntax in the conf file for header and footer. some websites say to use
<IfModule security2_module>
</IfModule>

another said
<Location "path">
</Location>

am i even on the right track here?

---

