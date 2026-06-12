---
title: "Mod_security configuration"
date: 2013-11-08
forum: Security
---

### Post by termvrl on 2013-11-08
Dear All,
i'm new to web server security. i have a few question on modsecurity and web server.
first, let me brief what i try to do. I have apache server running a DVWA web application on ubuntu 12.04 64bit.
I installed modsecurity on that server to detect and generated alert on attacks. Alert that generated from modsecurity than pass to a remote syslog server using rsyslog.
And i also want to monitor the web server nic and cpu usage, so that i can create a benchmark before and after implement modsecurity to web server.

My questions:
1) i want to monitor the nic and cpu usage for a period of time. Appreciate if you suggest scripts/tools for that. 
2) i noticed that logging for modsecurity quiet challenging. Anyone can share with me how to send modsecurity log/alert to remote server. What i have doned, using local rsyslog in web server, i take the modsecurlty_audit.log as input for rsyslog, and then send it to remote syslog server. My problem is, the log send line by line. 
> 192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: --e7b0fc0d-F--
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: HTTP/1.1 304 Not Modified
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Last-Modified: Tue, 30 Apr 2013 22:46:46 GMT
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: ETag: "1a06ac-2e4-4db9bc6a5a180"
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Accept-Ranges: bytes
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Content-Length: 0
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Vary: Accept-Encoding
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Keep-Alive: timeout=5, max=100
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Connection: Keep-Alive
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Content-Type: application/javascript
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: --e7b0fc0d-E--
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: --e7b0fc0d-H--
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Message: Rule 7fb26ee5aa30 [id "950901"][file "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"][line "77"] - Execution error - PCRE limits exceeded (-8): (null).


Appreciate your helps.
Thanks

---

### Post by bashiergui on 2013-11-09
What do you find challenging about the Modsecurity logs? This explains it pretty well [https://github.com/SpiderLabs/ModSecurity/wiki/ModSecurity-2-Data-Formats](https://github.com/SpiderLabs/ModSecurity/wiki/ModSecurity-2-Data-Formats).
What log aggregator are you feeding the logs to on the separate server?

Modsecurity has a community [http://www.modsecurity.org/contact/](http://www.modsecurity.org/contact/). You'll find lots of documentation & answers there.

---

### Post by termvrl on 2013-11-10
Hi Thanks for your response.

I managed to send modsecurity alert to SIEM server using rsyslog on my web server.
I was confused between to type of log provided by modsecurity, modsecurity_audit.log and error.log.
modsecurity log contain all information on GET request, rules that match and so on. 
error.log more to alert, same like snort ids. 

```

error.log

192.168.0.13|<131>Nov  9 22:57:23 ubuntu apache-errors: [Sat Nov 09 22:57:18 2013] [error] [client 192.168.0.111] ModSecurity: Warning. Pattern match "\\\\< ?script\\\\b" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "196"] [id "958051"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "<script"] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"] [hostname "192.168.0.13"] [uri "/dvwa/vulnerabilities/xss_r/"] [unique_id "Un8uTn8AAQEAAANuAhAAAAAC"]
11/10/2013 2:57:23 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<131>Nov  9 22:57:23 ubuntu apache-errors: [Sat Nov 09 22:57:18 2013] [error] [client 192.168.0.111] ModSecurity: Warning. Pattern match "\\\\balert\\\\b\\\\W*?\\\\(" at REQUEST_URI. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "393"] [id "958120"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "alert("] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"] [hostname "192.168.0.13"] [uri "/dvwa/vulnerabilities/xss_r/"] [unique_id "Un8uTn8AAQEAAANuAhAAAAAC"]
11/10/2013 2:57:23 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<131>Nov  9 22:57:23 ubuntu apache-errors: [Sat Nov 09 22:57:18 2013] [error] [client 192.168.0.111] ModSecurity: Warning. Pattern match "\\\\< ?script\\\\b" at REQUEST_URI. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "457"] [id "958119"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "<script"] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"] [hostname "192.168.0.13"] [uri "/dvwa/vulnerabilities/xss_r/"] [unique_id "Un8uTn8AAQEAAANuAhAAAAAC"]
11/10/2013 2:57:23 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<131>Nov  9 22:57:23 ubuntu apache-errors: [Sat Nov 09 22:57:18 2013] [error] [client 192.168.0.111] ModSecurity: Warning. Pattern match "<(a|abbr|acronym|address|applet|area|audioscope|b|base|basefront|bdo|bgsound|big|blackface|blink|blockquote|body|bq|br|button|caption|center|cite|code|col|colgroup|comment|dd|del|dfn|dir|div|dl|dt|em|embed|fieldset|fn|font|form|frame|frameset|h1|head|h ..." at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "556"] [id "973300"] [rev "2.2.5"] [msg "Possible XSS Attack Detected - HTML Tag Handler"] [data "<script>"] [hostname "192.168.0.13"] [uri "/dvwa/vulnerabilities/xss_r/"] [unique_id "Un8uTn8AAQEAAANuAhAAAAAC"]
11/10/2013 2:57:23 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<131>Nov  9 22:57:23 ubuntu apache-errors: [Sat Nov 09 22:57:18 2013] [error] [client 192.168.0.111] ModSecurity: Warning. Pattern match "(fromcharcode|alert|eval)\\\\s*\\\\(" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "646"] [id "973307"] [rev "2.2.5"] [msg "XSS Attack Detected"] [data "alert("] [hostname "192.168.0.13"] [uri "/dvwa/vulnerabilities/xss_r/"] [unique_id "Un8uTn8AAQEAAANuAhAAAAAC"]


```

and modsecurity_audit.log 

```

modsecurity_audit.log

--e7a90078-A--
[27/Oct/2013:09:55:46 --0700] Um1Fkn8AAQEAAANhBg8AAAAC 192.168.0.114 47114 192.168.0.13 80
--e7a90078-B--
GET /dvwa/vulnerabilities/xss_r/?name=%3Cscript%3Ealert%28%22Hacked%22%29%3C%2Fscript%3E HTTP/1.1
Host: 192.168.0.13
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:24.0) Gecko/20100101 Firefox/24.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://192.168.0.13/dvwa/vulnerabilities/xss_r/
Cookie: security=low; PHPSESSID=o5cnmkm1vhtectp7a5282vv896
Connection: keep-alive

--e7a90078-F--
HTTP/1.1 200 OK
X-Powered-By: PHP/5.3.10-1ubuntu3.8
Expires: Tue, 23 Jun 2009 12:00:00 GMT
Cache-Control: no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 1318
Keep-Alive: timeout=5, max=98
Connection: Keep-Alive
Content-Type: text/html;charset=utf-8

--e7a90078-E--

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">

    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />

        <title>Damn Vulnerable Web App (DVWA) v1.8 :: Vulnerability: Reflected Cross Site Scripting (XSS)</title>

        <link rel="stylesheet" type="text/css" href="../../dvwa/css/main.css" />

        <link rel="icon" type="\image/ico" href="../../favicon.ico" />

        <script type="text/javascript" src="../../dvwa/js/dvwaPage.js"></script>

    </head>

    <body class="home">
        <div id="container">

            <div id="header">

                <img src="../../dvwa/images/logo.png" alt="Damn Vulnerable Web App" />

            </div>

            <div id="main_menu">

                <div id="main_menu_padded">
                <ul><li onclick="window.location='../../.'" class=""><a href="../../.">Home</a></li><li onclick="window.location='../../instructions.php'" class=""><a href="../../instructions.php">Instructions</a></li><li onclick="window.location='../../setup.php'" class=""><a href="../../setup.php">Setup</a></li></ul><ul><li onclick="window.location='../../vulnerabilities/brute/.'" class=""><a href="../../vulnerabilities/brute/.">Brute Force</a></li><li onclick="window.location='../../vulnerabilities/exec/.'" class=""><a href="../../vulnerabilities/exec/.">Command Execution</a></li><li onclick="window.location='../../vulnerabilities/csrf/.'" class=""><a href="../../vulnerabilities/csrf/.">CSRF</a></li><li onclick="window.location='../../vulnerabilities/captcha/.'" class=""><a href="../../vulnerabilities/captcha/.">Insecure CAPTCHA</a></li><li onclick="window.location='../../vulnerabilities/fi/.?page=include.php'" class=""><a href="../../vulnerabilities/fi/.?page=include.php">File Inclusion</a></li><li onclick="window.location='../../vulnerabilities/sqli/.'" class=""><a href="../../vulnerabilities/sqli/.">SQL Injection</a></li><li onclick="window.location='../../vulnerabilities/sqli_blind/.'" class=""><a href="../../vulnerabilities/sqli_blind/.">SQL Injection (Blind)</a></li><li onclick="window.location='../../vulnerabilities/upload/.'" class=""><a href="../../vulnerabilities/upload/.">Upload</a></li><li onclick="window.location='../../vulnerabilities/xss_r/.'" class="selected"><a href="../../vulnerabilities/xss_r/.">XSS reflected</a></li><li onclick="window.location='../../vulnerabilities/xss_s/.'" class=""><a href="../../vulnerabilities/xss_s/.">XSS stored</a></li></ul><ul><li onclick="window.location='../../security.php'" class=""><a href="../../security.php">DVWA Security</a></li><li onclick="window.location='../../phpinfo.php'" class=""><a href="../../phpinfo.php">PHP Info</a></li><li onclick="window.location='../../about.php'" class=""><a href="../../about.php">About</a></li></ul><ul><li onclick="window.location='../../logout.php'" class=""><a href="../../logout.php">Logout</a></li></ul>
                </div>

            </div>

            <div id="main_body">

                
<div class="body_padded">
    <h1>Vulnerability: Reflected Cross Site Scripting (XSS)</h1>

    <div class="vulnerable_code_area">

        <form name="XSS" action="#" method="GET">
            <p>What's your name?</p>
            <input type="text" name="name">
            <input type="submit" value="Submit">
        </form>

        <pre>Hello <script>alert("Hacked")</script></pre>

    </div>

    <h2>More info</h2>

    <ul>
        <li><a href="http://hiderefer.com/?http://ha.ckers.org/xss.html" target="_blank">http://ha.ckers.org/xss.html</a></li>
        <li><a href="http://hiderefer.com/?http://en.wikipedia.org/wiki/Cross-site_scripting" target="_blank">http://en.wikipedia.org/wiki/Cross-site_scripting</a></li>
        <li><a href="http://hiderefer.com/?http://www.cgisecurity.com/xss-faq.html" target="_blank">http://www.cgisecurity.com/xss-faq.html</a></li>
    </ul>
</div>

                <br />
                <br />
                

            </div>

            <div class="clear">
            </div>

            <div id="system_info">
                <input type="button" value="View Help" class="popup_button" onClick="javascript:popUp( '../../vulnerabilities/view_help.php?id=xss_r&security=low' )"> <input type="button" value="View Source" class="popup_button" onClick="javascript:popUp( '../../vulnerabilities/view_source.php?id=xss_r&security=low' )"> <div align="left"><b>Username:</b> admin<br /><b>Security Level:</b> low<br /><b>PHPIDS:</b> disabled</div>
            </div>

            <div id="footer">

                <p>Damn Vulnerable Web Application (DVWA) v1.8</p>

            </div>

        </div>

    </body>

</html>
--e7a90078-H--
Message: Warning. Match of "streq %{SESSION.IP_HASH}" against "TX:ip_hash" required. [file "/etc/modsecurity/activated_rules/modsecurity_crs_16_session_hijacking.conf"] [line "35"] [id "981059"] [msg "Warning - Sticky SessionID Data Changed - IP Address Mismatch."]
Message: Warning. Match of "streq %{SESSION.UA_HASH}" against "TX:ua_hash" required. [file "/etc/modsecurity/activated_rules/modsecurity_crs_16_session_hijacking.conf"] [line "36"] [id "981060"] [msg "Warning - Sticky SessionID Data Changed - User-Agent Mismatch."]
Message: Warning. Operator EQ matched 2 at TX:sticky_session_anomaly. [file "/etc/modsecurity/activated_rules/modsecurity_crs_16_session_hijacking.conf"] [line "37"] [id "981061"] [msg "Possible Session Hijacking - IP Address and User-Agent Mismatch."]
Message: Warning. Pattern match "^[\\d.:]+$" at REQUEST_HEADERS:Host. [file "/etc/modsecurity/activated_rules/modsecurity_crs_21_protocol_anomalies.conf"] [line "98"] [id "960017"] [rev "2.2.5"] [msg "Host header is a numeric IP address"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/IP_HOST"] [tag "WASCTC/WASC-21"] [tag "OWASP_TOP_10/A7"] [tag "PCI/6.5.10"] [tag "http://technet.microsoft.com/en-us/magazine/2005.01.hackerbasher.aspx"]
Message: Operator GE matched 5 at TX:restricted_char_count. [file "/etc/modsecurity/activated_rules/modsecurity_crs_40_experimental.conf"] [line "52"] [id "960023"] [rev "2.0.10"] [msg "Restricted Character Anomaly Detection Alert - Total # of special characters exceeded"] [data "5"]
Message: Pattern match "\\W{4,}" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_40_experimental.conf"] [line "57"] [id "960024"] [rev "2.0.10"] [msg "Restricted Character Anomaly Detection Alert - Repetative Non-Word Characters"] [data "\x22)</"]
Message: Rule 7f56159fd280 [id "950901"][file "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"][line "77"] - Execution error - PCRE limits exceeded (-8): (null).
Message: Rule 7f56159fd280 [id "950901"][file "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"][line "77"] - Execution error - PCRE limits exceeded (-8): (null).
Message: Warning. Pattern match "(?i:([\\s'\"`\xc2\xb4\xe2\x80\x99\xe2\x80\x98\\(\\)]*)?([\\d\\w]+)([\\s'\"`\xc2\xb4\xe2\x80\x99\xe2\x80\x98\\(\\)]*)?(?:=|<=>|r?like|sounds\\s+like|regexp)([\\s'\"`\xc2\xb4\xe2\x80\x99\xe2\x80\x98\\(\\)]*)?\\2|([\\s'\"`\xc2\xb4\xe2\x80\x99\xe2\x80\x98\ ..." at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"] [line "77"] [id "950901"] [rev "2.2.5"] [msg "SQL Injection Attack"] [data "script>alert"] [severity "CRITICAL"] [tag "WEB_ATTACK/SQL_INJECTION"] [tag "WASCTC/WASC-19"] [tag "OWASP_TOP_10/A1"] [tag "OWASP_AppSensor/CIE1"] [tag "PCI/6.5.2"]
Message: Warning. Pattern match "\\W{4,}" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"] [line "155"] [id "960024"] [rev "2.2.5"] [msg "SQL Character Anomaly Detection Alert - Repetative Non-Word Characters"] [data "\x22)</"]
Message: Warning. Pattern match "([\\~\\!\\@\\#\\$\\%\\^\\&\\*\\(\\)\\-\\+\\=\\{\\}\\[\\]\\|\\:\\;\"\\'\\\xc2\xb4\\\xe2\x80\x99\\\xe2\x80\x98\\`\\<\\>].*){4,}" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"] [line "171"] [id "981173"] [rev "2.2.5"] [msg "Restricted SQL Character Anomaly Detection Alert - Total # of special characters exceeded"] [data ">"]
Message: Warning. Pattern match "(?i:(?:[\"'`\xc2\xb4\xe2\x80\x99\xe2\x80\x98]\\s*?\\*.+(?:x?or|div|like|between|and|id)\\W*?[\"'`\xc2\xb4\xe2\x80\x99\xe2\x80\x98]\\d)|(?:\\^[\"'`\xc2\xb4\xe2\x80\x99\xe2\x80\x98])|(?:^[\\w\\s\"'`\xc2\xb4\xe2\x80\x99\xe2\x80\x98-]+(?<=and\\s)(?<=or|xor ..." at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"] [line "257"] [id "981243"] [msg "Detects classic SQL injection probings 2/2"] [data ">alert(\x22H"] [severity "CRITICAL"] [tag "WEB_ATTACK/SQLI"]
Message: Warning. Pattern match "\\balert\\b\\W*?\\(" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "148"] [id "958052"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "alert("] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"]
Message: Warning. Pattern match "\\< ?script\\b" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "196"] [id "958051"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "<script"] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"]
Message: Warning. Pattern match "\\balert\\b\\W*?\\(" at REQUEST_URI. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "393"] [id "958120"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "alert("] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"]
Message: Warning. Pattern match "\\< ?script\\b" at REQUEST_URI. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "457"] [id "958119"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "<script"] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"]
Message: Warning. Pattern match "<(a|abbr|acronym|address|applet|area|audioscope|b|base|basefront|bdo|bgsound|big|blackface|blink|blockquote|body|bq|br|button|caption|center|cite|code|col|colgroup|comment|dd|del|dfn|dir|div|dl|dt|em|embed|fieldset|fn|font|form|frame|frameset|h1|head|h ..." at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "556"] [id "973300"] [rev "2.2.5"] [msg "Possible XSS Attack Detected - HTML Tag Handler"] [data "<script>"]
Message: Warning. Pattern match "(fromcharcode|alert|eval)\\s*\\(" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "646"] [id "973307"] [rev "2.2.5"] [msg "XSS Attack Detected"] [data "alert("]
Message: Warning. Pattern match "(?i:<script.*?>)" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "757"] [id "973331"] [rev "2.2.5"] [msg "IE XSS Filters - Attack Detected"] [data "<script>"]
Message: Warning. Match of "eq 1" against "&ARGS:CSRF_TOKEN" required. [file "/etc/modsecurity/activated_rules/modsecurity_crs_43_csrf_protection.conf"] [line "31"] [id "981143"] [msg "CSRF Attack Detected - Missing CSRF Token."]
Message: Warning. String match "<script>alert(\"Hacked\")</script>" at RESPONSE_BODY. [file "/etc/modsecurity/activated_rules/modsecurity_crs_55_application_defects.conf"] [line "175"] [id "1"] [msg "Potentially Malicious Meta-Characters in User Data Not Properly Output Encoded."] [data "<script>alert(\x22Hacked\x22)</script>"]
Message: Warning. String match within "\n<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\">\n\n<html xmlns=\"http://www.w3.org/1999/xhtml\">\n\n\t<head>\n\t\t<meta http-equiv=\"Content-Type\" content=\"text/html; charset=UTF-8\" />\n\n\t\t<title>Damn Vulnerable Web App (DVWA) v1.8 :: Vulnerability: Reflected Cross Site Scripting (XSS)</title>\n\n\t\t<link rel=\"stylesheet\" type=\"text/css\" href=\"../../dvwa/css/main.css\" />\n\n\t\t<link rel=\"icon\" type=\"\\image/ico\" href=\"../../favicon.ico\" />\n\n\t\t<script type=\"text/javascript\" src=\"../../dvwa/js/dvwaPage.js\"></script>\n\n\t</head>\n\n\t<body class=\"home\">\n\t\t<div id=\"container\">\n\n\t\t\t<div id=\"header\">\n\n\t\t\t\t<img src=\"../../dvwa/images/logo.png\" alt=\"Damn Vulnerable Web App\" />\n\n\t\t\t</div>\n\n\t\t\t<div id=\"main_menu\">\n\n\t\t\t\t<div id=\"main_menu_padded\">\n\t\t\t\t<ul><li onclick=\"window.location='../../.'\" class=\"\"><a href=\"../../.\">Home</a></li><li on
Message: Warning. Match of "contains no-store" against "RESPONSE_HEADERS:Cache-Control" required. [file "/etc/modsecurity/activated_rules/modsecurity_crs_55_application_defects.conf"] [line "121"] [id "981240"] [msg "AppDefect: Cache-Control Response Header Missing 'no-store' flag."] [data "Cache-Control: no-cache, must-revalidate"] [tag "WASCTC/WASC-15"] [tag "MISCONFIGURATION"] [tag "http://websecuritytool.codeplex.com/wikipage?title=Checks#http-cache-control-header-no-store"]
Message: Warning. Operator GE matched 5 at TX:inbound_anomaly_score. [file "/etc/modsecurity/activated_rules/modsecurity_crs_60_correlation.conf"] [line "37"] [id "981204"] [msg "Inbound Anomaly Score Exceeded (Total Inbound Score: 68, SQLi=8, XSS=35): IE XSS Filters - Attack Detected"]
Apache-Handler: application/x-httpd-php
Stopwatch: 1382892946877201 34906 (- - -)
Stopwatch2: 1382892946877201 34906; combined=22574, p1=989, p2=16825, p3=151, p4=3942, p5=564, sr=174, sw=103, l=0, gc=0
Response-Body-Transformed: Dechunked
Producer: ModSecurity for Apache/2.6.3 (http://www.modsecurity.org/); OWASP_CRS/2.2.5.
Server: Apache/2.2.22 (Ubuntu)
WebApp-Info: "default" "o5cnmkm1vhtectp7a5282vv896" ""

--e7a90078-Z--


```

from this log can we simplify/re-formatted it to more general form? How?

for example, 
```
AttackDate:9/11/2013 , AttackTime:22:57:18 , AttackType: XSS Attack ,  SourceIP:192.168.0.111 , TargetIP:192.168.0.13 , SourcePort:47114 ,  TargetPort:80 , Severity: High
```

Thanks again for your help.
Term

---

### Post by sandyd on 2013-11-10
you need sed
something like maybe
```
cat test4 | sed '/Received from/d' | sed 's/\(\)|<[1-9]*>\([A-z]*\).*/\1, Month: \2/'
```

---

### Post by termvrl on 2013-11-12
Thanks for response...
i am exploring sed. 
after googling around, i found that modsec also have console panel called waf-fle.

---

