---
title: "virtual host in apache2"
date: 2010-03-14
forum: Server Platforms
---

### Post by ragit on 2010-03-14
[SIZE=2]hey everybody,

I have sold this problem previously but it had a side affect (i know not do any SSL any more)

Now I have made a clean install.

* clean install apache2 inc. SSL

/etc/apache2/sites-available shows by default

default.conf
default-ssl.conf 

Now i have added my virtual hosts in this way.

djuw*a.nl.conf
[/SIZE]<VirtualHost *:*>
ServerName [www.djuw*a.nl]("http://www.djuwya.nl")
ServerAlias djuwya.nl *.djuw*a.nl
DocumentRoot /var/www/djuw*a.nl
</VirtualHost>

[SIZE=2]haar*enik.nl.conf
[/SIZE]<VirtualHost *>
ServerName [www.haar*nik.nl]("http://www.haarenik.nl")
ServerAlias haar*nik.nl *.haar*nik.nl
DocumentRoot /var/www/haar*nik.nl
</VirtualHost>

[SIZE=2]edi-fact*ur.com.conf
[/SIZE]<VirtualHost *>
ServerName [www.edi-fact*ur.com]("http://www.edi-factuur.com")
ServerAlias edi-fact*ur.com *.edifact*ur.com
DocumentRoot /var/www/edi-fact*ur.com
</VirtualHost>


the problem now is, it does not separate the web pages. 
when I go to haareni*.nl it displays edi-fa*tuur.com and if I point to the IP adres it gives the web page of haar*nik.nl


but SSL is working!

what is it that i`m missing?#-o

there is so much to find about apache and apache2 and everybody has its own way of doing things, this makes it really confusing!

please help!!!!

---

### Post by Ryan Dwyer on 2010-03-14
Please don't butcher your post by putting asterisks everywhere. It makes it hard to read. I've already established your hosts are djuwya.nl, haarenik.nl and edi-factuur.com.

Change all of your VirtualHost containers to say <VirtualHost *:80>, unless you actually need SSL. You said you're not doing SSL any more. And make sure you've got NameVirtualHost * set in your main config file.

---

### Post by ragit on 2010-03-14
sorry for the * but i dont like if you google for the site and this forum is in the list...
I have made the given changes but no result. If i go to the different sites i still get 1 page.

---

### Post by cdenley on 2010-03-15
Did you enable the new site configurations with a2ensite, reload apache, then clear your browser cache?
```

ls -l /etc/apache2/sites-enabled
sudo /etc/init.d/apache2 reload
echo -e "GET / HTTP/1.0\nHost: site1.com\n"|nc 127.0.0.1 80
echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc 127.0.0.1 80

```
Replace site1.com and site2.com with the actual hostnames.

---

### Post by ragit on 2010-03-16
yes, but no effect... 

this is my ports.conf

No strange things are there?


------------ports.conf----------------
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

---

### Post by cdenley on 2010-03-16
Post the output from the commands I posted.

---

### Post by ragit on 2010-03-16
ls -l /etc/apache2/sites-enabled
totaal 0
lrwxrwxrwx 1 root root 30 2010-03-15 22:17 default-ssl -> ../sites-available/default-ssl
lrwxrwxrwx 1 root root 43 2010-03-16 00:26 djuwya.nl.conf -> /etc/apache2/sites-available/djuwya.nl.conf
lrwxrwxrwx 1 root root 49 2010-03-15 23:54 edi-factuur.com.conf -> /etc/apache2/sites-available/edi-factuur.com.conf
lrwxrwxrwx 1 root root 45 2010-03-15 23:54 haarenik.nl.conf -> /etc/apache2/sites-available/haarenik.nl.conf


sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          [Tue Mar 16 14:03:29 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [ OK ]

---

### Post by cdenley on 2010-03-16
I was more interested in the other two commands I posted. Also, using the "CODE" tags makes it easier to read command output.
```

[noparse]
[CODE]
output goes here

```
[/noparse]
[/CODE]

---

### Post by ragit on 2010-03-16
this is the output for the first
```

root@ip13-241:/home/ragit# echo -e "GET / HTTP/1.0\nHost: edi-factuur.com\n"|nc 127.0.0.1 80
HTTP/1.1 200 OK
Date: Tue, 16 Mar 2010 13:37:10 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Tue, 09 Mar 2010 21:14:51 GMT
ETag: "18ef2-3868-48164ac1ae8c0"
Accept-Ranges: bytes
Content-Length: 14440
Vary: Accept-Encoding
Connection: close
Content-Type: text/html

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
  PUBLIC "-//W3C//DTD XHTML 1.1 plus MathML 2.0//EN" "http://www.w3.org/TR/MathML2/dtd/xhtml-math11-f.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"><!--This file was converted to xhtml by OpenOffice.org - see http://xml.openoffice.org/odf2xhtml for more info.--><head profile="http://dublincore.org/documents/dcmi-terms/"><meta http-equiv="Content-Type" content="text/html; charset=utf-8"/><title xml:lang="en-US">- no title specified</title><meta name="DCTERMS.title" content="" xml:lang="en-US"/><meta name="DCTERMS.language" content="en-US" scheme="DCTERMS.RFC4646"/><meta name="DCTERMS.source" content="http://xml.openoffice.org/odf2xhtml"/><meta name="DCTERMS.creator" content="admin"/><meta name="DCTERMS.issued" content="2010-03-05T21:10:00" scheme="DCTERMS.W3CDTF"/><meta name="DCTERMS.contributor" content="admin"/><meta name="DCTERMS.modified" content="2010-03-05T21:17:00" scheme="DCTERMS.W3CDTF"/><meta name="DCTERMS.provenance" content="" xml:lang="en-US"/><meta name="DCTERMS.subject" content="," xml:lang="en-US"/><link rel="schema.DC" href="http://purl.org/dc/elements/1.1/" hreflang="en"/><link rel="schema.DCTERMS" href="http://purl.org/dc/terms/" hreflang="en"/><link rel="schema.DCTYPE" href="http://purl.org/dc/dcmitype/" hreflang="en"/><link rel="schema.DCAM" href="http://purl.org/dc/dcam/" hreflang="en"/><base href="."/><style type="text/css">
        @page { size: 20.999cm 29.699cm; margin-top: 2.499cm; margin-bottom: 2.499cm; margin-left: 2.499cm; margin-right: 2.499cm }
        table { border-collapse:collapse; border-spacing:0; empty-cells:show }
        td, th { vertical-align:top; font-size:12pt;}
        h1, h2, h3, h4, h5, h6 { clear:both }
        ol, ul { margin:0; padding:0;}
        li { list-style: none; margin:0; padding:0;}
        li span.odfLiEnd { clear: both; line-height:0; width:0; height:0; margin:0; padding:0; }
        span.footnodeNumber { padding-right:1em; }
        * { margin:0; }
        .gr1 { font-size:11pt; line-height:115%; vertical-align:top; }
        .gr2 { font-size:11pt; line-height:115%; padding-top:0.125cm; padding-bottom:0.125cm; padding-left:0.25cm; padding-right:0.25cm; vertical-align:top; }
        .P1 { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; text-align:center ! important; }
        .P2 { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; }
        .P3 { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; text-align:center ! important; }
        .P4 { font-size:18pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; text-align:center ! important; }
        .Standard { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; }
        .T1 { font-size:30pt; }
        <!-- ODF styles with no properties representable as CSS -->
        .Endnote_20_Symbol .Footnote_20_Symbol { }
        </style></head><body dir="ltr" style="max-width:20.999cm;margin-top:2.499cm; margin-bottom:2.499cm; margin-left:2.499cm; margin-right:2.499cm; "><div class="P2"><p>Â </p><div style="height: 5.384cm;width: 16.306cm;" id="Picture_1" class="P4"><p><img width="713" height="235" alt="" src="data:image/*;base64,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"/></p></div></div><p class="P1"><span

```
this is the second
```

root@ip13-241:/home/ragit# echo -e "GET / HTTP/1.0\nHost: haarenik.nlHTTP/1.1 200 OK1 80
Date: Tue, 16 Mar 2010 13:38:35 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Tue, 09 Mar 2010 21:14:51 GMT
ETag: "18ef2-3868-48164ac1ae8c0"
Accept-Ranges: bytes
Content-Length: 14440
Vary: Accept-Encoding
Connection: close
Content-Type: text/html

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
  PUBLIC "-//W3C//DTD XHTML 1.1 plus MathML 2.0//EN" "http://www.w3.org/TR/MathML2/dtd/xhtml-math11-f.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"><!--This file was converted to xhtml by OpenOffice.org - see http://xml.openoffice.org/odf2xhtml for more info.--><head profile="http://dublincore.org/documents/dcmi-terms/"><meta http-equiv="Content-Type" content="text/html; charset=utf-8"/><title xml:lang="en-US">- no title specified</title><meta name="DCTERMS.title" content="" xml:lang="en-US"/><meta name="DCTERMS.language" content="en-US" scheme="DCTERMS.RFC4646"/><meta name="DCTERMS.source" content="http://xml.openoffice.org/odf2xhtml"/><meta name="DCTERMS.creator" content="admin"/><meta name="DCTERMS.issued" content="2010-03-05T21:10:00" scheme="DCTERMS.W3CDTF"/><meta name="DCTERMS.contributor" content="admin"/><meta name="DCTERMS.modified" content="2010-03-05T21:17:00" scheme="DCTERMS.W3CDTF"/><meta name="DCTERMS.provenance" content="" xml:lang="en-US"/><meta name="DCTERMS.subject" content="," xml:lang="en-US"/><link rel="schema.DC" href="http://purl.org/dc/elements/1.1/" hreflang="en"/><link rel="schema.DCTERMS" href="http://purl.org/dc/terms/" hreflang="en"/><link rel="schema.DCTYPE" href="http://purl.org/dc/dcmitype/" hreflang="en"/><link rel="schema.DCAM" href="http://purl.org/dc/dcam/" hreflang="en"/><base href="."/><style type="text/css">
        @page { size: 20.999cm 29.699cm; margin-top: 2.499cm; margin-bottom: 2.499cm; margin-left: 2.499cm; margin-right: 2.499cm }
        table { border-collapse:collapse; border-spacing:0; empty-cells:show }
        td, th { vertical-align:top; font-size:12pt;}
        h1, h2, h3, h4, h5, h6 { clear:both }
        ol, ul { margin:0; padding:0;}
        li { list-style: none; margin:0; padding:0;}
        li span.odfLiEnd { clear: both; line-height:0; width:0; height:0; margin:0; padding:0; }
        span.footnodeNumber { padding-right:1em; }
        * { margin:0; }
        .gr1 { font-size:11pt; line-height:115%; vertical-align:top; }
        .gr2 { font-size:11pt; line-height:115%; padding-top:0.125cm; padding-bottom:0.125cm; padding-left:0.25cm; padding-right:0.25cm; vertical-align:top; }
        .P1 { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; text-align:center ! important; }
        .P2 { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; }
        .P3 { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; text-align:center ! important; }
        .P4 { font-size:18pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; text-align:center ! important; }
        .Standard { font-size:11pt; line-height:115%; margin-bottom:0.353cm; margin-top:0cm; font-family:Calibri; }
        .T1 { font-size:30pt; }
        <!-- ODF styles with no properties representable as CSS -->
        .Endnote_20_Symbol .Footnote_20_Symbol { }
        </style></head><body dir="ltr" style="max-width:20.999cm;margin-top:2.499cm; margin-bottom:2.499cm; margin-left:2.499cm; margin-right:2.499cm; "><div class="P2"><p>Â </p><div style="height: 5.384cm;width: 16.306cm;" id="Picture_1" class="P4"><p><img width="713" height="235" alt="" src="data:image/*;base64,iVBORw0KGgoAAAANSUhEUgAAAcMAAACVCAIAAACrRAbXAAAAAXNSR0IArs4c6QAAIENJREFUeF7tnXlcU2e+/w9JyMYSlrDIFlbZRAQRpFQFRW1r3a21i7XtTKfTWjv93Zne6TKva3tneud1p85tO+p00VrrVm3VWi3VFlcQQUA2WQTZl7AlAQIkJITkd5KQsAW3Uw2Bz/lLc86zfN/frx+f8zzf5zlWGo2GoHBZWVm99957FCpAURAAARAwMwFSxCgqIc3MFqB5EAABELB8AlBSy/chLAABEDA3ASipuT2A9kEABCyfAJTU8n0IC0AABMxNAEpqbg+gfRAAAcsnACW1fB/CAhAAAXMTgJKa2wNoHwRAwPIJQEkt34ewAARAwNwEoKTm9gDaBwEQsHwCUFLL9yEsAAEQMDcBKKm5PYD2QQAELJ8AlNTyfQgLQAAEzE0ASmpuD6B9EAAByycAJbV8H8ICEAABcxOAkprbA2gfBEDA8glASS3fh7AABEDA3ASgpOb2ANoHARCwfAJQUsv3ISwAARAwNwEoqbk9gPZBAAQsnwCU1PJ9CAtAAATMTQBKam4PoH0QAAHLJwAltXwfwgIQAAFzE4CSmtsDaB8EQMDyCUBJLd+HsAAEQMDcBKCk5vYA2gcBELB8AlBSy/chLAABEDA3ASipuT2A9kEABCyfAJTU8n0IC0AABMxNAEpqbg+gfRAAAcsnACW1fB/CAhAAAXMTgJKa2wNoHwRAwPIJQEkt34ewAARAwNwEoKTm9gDaBwEQsHwCUFLL9yEsAAEQMDcBKKm5PYD2QQAELJ8AlNTyfXj/LXAKXrbpuUTB/OWPhLsFBC1eFO00Y/mWPz0TrWuZy+Xe/x6gBRCY2ASsNBoNlR5aWVm99957VGpAWYsgELB04wJfdz7nZtq+7BsabuJj/hkHL/dqNVTGZjtJJJIJawV35oZXVwcyemRKwoph1V147OufaxQTtrfomFkIkCJGVQmploeSmsXzD7JRB59Ir2APn5bqmx5z14eqi0v7+OHu6jZJP8vRg1m2+7NzEnJYKpPJ7rpPdFtbz5lr1i/yszH1aqRRdNSV5WdnZJWJ+u+kapazwN/b1Y7W19VaV9kkHRgs4770tZcFxf/3xcVu7Q/ssHWvLiPO/PNoqfpO6sQzU4QAlHSKONp8ZvJmL4nobLGKi5sf5MEY242W9E8+P99J/k63s2N1Oyb94YUYB4LoldzIPnIkrW3cbtOmzXt+40Ln2p/OdXjw+5paOvoZXFtHFw8vga+XC9fQjlQqtbe3Jwh5483KtpK0nwpFBnkcqpjmNGNx4gy6esDTidZUWVVbWyeie4cEOjvYEKWnUysVBDNs6SPcnJO5xkEzKa0r+/d/fr7LfFDR8kQjACWdaB6ZjP1x4vO7RGJeRGLSrIhAP0e21TAjRZn/3vlLO/mDlbU1J3bjm8nehpsNZz/Yk6EyxcM67Ik/PBGiuHbw0x+rTT5AMN1nLVy8INrfwVpffkClojMYhKa37uK3h9Lqlbof7UOXrlwQxFMJM0/+cK1tjMbaxz63gn30QNrYoTJv4curej//+upk9BVsujcC1JUUK073Rn4qlZKIyLGgRnL9wrH9u789euzL9LqhN2NZDznWs+fxrDT9/b4e/GFYOLbOJiExY59aNa3y8IfbdTLqlvibP7/9H5vmTxsuz4SypeDM/k/+5/2/bj+W0yRTE1oZ1aq1jSDphbff3rx66erNb299LYlI37Vjx+7jJmSUfFiaXU73izDVha7evqnkPtj6QAhASR8IZotvhM7h+CevSHQUNVSLz5fVGweeFbkDBJ3pN3MWKaJlja3D7OyRmn6553Xl7vn0RLlezDyiI7zYTDvfpHWPeJpgpJYU/7T7w7/+7bOUEpGsXz9+VUhUPnNn8q0kN7Ou1Q4bibJCl2/+z3ff+Y+Ny+JDHUhdZkb6uZleTWVZm5imsHgPwQDzEsDavXn5W1TrTL6bLc8zfuacsJnu2lX75kvfnm+sqazUqSJfIFDIA5753Tw3OrmeX3nq84N50tHWWdHpYav/GNf8f8b3fpZX9LyokODwoP6sj764OKbA8ApsIje8lNBxttx39cPuNELReGHvnrQWY+IJPWDxi6tjPWyGiaSy8tS2g3ljVquck19ZT3z76VmxafY2/vMffzR+Op+tG2Qoq09/0xS1IYbRWJx5NjWv5Y7WvizKqeislgD1t3soKSLprgjYxCyeb+cWPD+A13h+n3DWcqsLh7KLRSJyycnaWt3ff8uUOlbEk6+vCVEXH/74WPnIec2wdRvdz+0/30F2hRc8L4QpbBHW1ImNkwhc12Dvafa20qJrNWr36EWzuWXncuxXvBwvPrb7XFP4k6/4Zn/xU82AvkquZ3RCXKCdvCbnXE6DfkZ12EX3W/Hac675H+42MX9K0D3nP/FYkHVbeXbG1XJjwgDXNTAo8qHkuX62ypbCCz+dzm5ADtVdhYwlPAwltQQvTZ4+0sPX/+EhVbPax82L2Z1fbxMVrLlx4WJBQ7eK4+whcJHnn8nVxC4MFF/PrWofR24il673sbf1dqWLy/NzC0qalU4B8x6do0k7dq6iiyxin/Tylof4DHJeVJK9a/tpIcGPWhiuvJ5VMro+lm/C8iXxIW4M1QCLpV+YUkoqctMupBW2jNO0fdiKjauiuDUndn5TOHYdihP51OYFPd9/eqrK5LjTJnrdS0vDeaqSb7cdLaOUgj15wmESWQIlnUTOnMimcLl8T0+2JnJFfFtuTnO7X4igkR61JtKe6G04c2RPkZxPE4l6vZe9tpiot4kJVQnljtZle/+dKjRlU9yyZcKU012+0RGOBDMo0Elak5t2tW5I2ugBq7Y8G8kj6tJ3ZtBXJ6pP7TrXYqIeTtjal9fO4Jmc6NeoesXNjcLWju5eeT/D1snVUyCYxmNqelsbxDJlr6yf6Cr5MbV0mJwKlm95tPfIZ+fHT9wiCJZ/mHdLaaXMZ+lyz8unMnsnssPQt7sjACW9O154+p4J0Ox8H16b7N6Uk1Ftn7goxtvFnqWdkhRe+PZajyQvT7/WFPnUO6umW8tLv/vHFcGWZ3mXth0uGpsBygqODGgsLB1XiLjzX3ozyUPVWVNWr+C799e0BzwUTs7KqjpKUw58VzCYFipY/sbz0ey2kitpaVdL2sisUX7QrFnhQb7eHm6OXMaIRABCJRM1VpVcrbcNUpw+dV3XIXb00y94Z336Q7WeB2/hc4+KDx4uHNvZsbxokU/9eZVf8y879mbeclr3nkmjoBkIQEnNAH2yN8lIWPN4y812b3GH/WK/XsX0SFeCzuWyrWlqmTD1+IniGrEi/vm/LBHoOAgv7M2hCZhSqZpNPuPgGzHHj9FS023jNtDY5Ogou5TfzrG10V5cDnkpyn/4NpOcUyUEERHd1ZJpwZ72NuT+KK7uJofNYfc1VKmnzw23bUo/ddNl6ZIQMi1/+NWVt/fjU3XkL/zkNdFFx38ZZwRpH7FkSbCxqBXLnu9gw1Bbaeg92o1YarWaRqNZ89yZN77efrqJrC181QZeTqVLoq9K2NDcqXENmuFh21eTeYM9rev0+aqRXWDP+82fF3qRvzVfMuybmuwBMRXsg5JOBS8/QBu5/MUJUcX5meIOpUvCxo1JXqzbNN5W3+XqwzPxUH9FmcQn1I2tvyXv6WHa2tKlBfs/0o8DWQHzlsaFhAV5mGigp/jHE71RG+I8xyQr9RQe/OeJSrL47Gc3Mr/ZnxMYs3b+IyEe3blffZJizMwiCJ9l+q1Wt7tqz7yvzc+3TVgQllPh9PLv4pxGlJDXp+796spotWY9/Ju3Fmml1Lgp4XbN4P7EJ0BdSZFPOvG9/AB7KBOlp6c3i1RhT77xW72MqpWteYe3vU9ef73Q2FJW2zOyN9acvoxdO/b9WNbR09k1fMNSp+j8rt27D5/KaZKTJTjq5uKq7mH3FVXpJw/t+mjPL0W1DeLhK+x9VSm7jxX01NfWj2ipo+SHr3afuyYcnHm9linxX7bqhfXLHGjkBiuHkOjA4d2qT/nkbzuO5bUa6pXVnN1/pnpYOr68+uK+nWdr9WXsYvxce5TNZ7b/9yff5RpWq9TSm2f27R8jo+Tjiryb+k7w/cmJXlwgoCcAJUUk6AkwuFztEnhfnyrsiddWBnF0P7am7/j7Z6fKdXOa6ryC3OKv/7kzpWqYxim65E5O4pqyluKsTz/++KJeY1StuWcL7Vb+caVvTd5Pu3dqf7UPigywGzPGVDRkfv/1nl2XGw1O6Mg5cCC3ixhoLT27/+MT5UOL8LK2ivqmyxezDYtEVSkHTxa29hDuDg6kQtpOjwrTVcHm6PtNDIiLT12t00p3b8l3H+3LqL66/9M048IVx5bZLaMz9Y8KXFWNN7R/0HSWphzN1Y5BJVd3f3ToaovprawyxaBCu3mHjJyQRShNYQJQ0sno/Hs4MtQ9LjbQmkYjXOMWzXFlyWVKMpmztzwzi0zx9AsI0IVJz7VrpXFPr3NMzxp6k9Y0VhEhM5xmWUlzyUPrtMIir82vYsckJ0d4SSrztJrT2zcmq3Mkc4VcYepgpoHCS4b1JYLwDIwa3INvLBsQGUjOhbLpdDJriUOuN2lv9Mm1I2D9Nc2NIe/ur7rwfaleEaVpOZWGBCfX0LgFAnf9c3Q6h207WMYpKsiVIFpKMptvExb9HeVnvzqSiXSoyfjP555sgpLeE7YJXugejrhrb6wRq5lMm9CZoV0//+8/jlxpkddlpDRNDxEQNVVVRqXLTqsKfDbZ2/h3jsCLH7D2Gd7NXAUzYf0CuxvZjS5RwdqJ046c02lDsnZLYFVC7RkoY6/mK9eNiuYdFDMyVoNmBthpi1gzGKSeWQfOjB1ZgX2IwM/OTnjzmnFBfiCvUru+pLscZ8/x6xLp/lpR2+caqJdp9zkhroS6Jv/irc6JopUc//D9//nX4SxVVGzQBA8EdO+BEYCSPjDUE7kh59jVc71YYXNi5k334EU89fbWFxI9ejW0gIGbVdql8qFL05j66Qd/u2h8T6ap61J2bEtVRM2NWTCtdneqZmaQjf7pLrFRtm5nuaNMJtGP7tSDG5UGS0hzyo0pqYLpc4bXExwRaEt0XrtS3k8eNk7esPILix8ezNxZgeSYs648d0TvJV2GzCWyVJdE10N5VTkjJFF7+ErA3HBnoqvgUvYtzy5V9/SwI5a/8tZfXloS5e1wO9twf4oQgJJOEUff2kzxtfx2a+u8dJWbBzl3Tr7kk1OkN05lFHT0jtnwQ84ckOc+GarrqS+s6+29kXFd2Jh69HwTh3XrxX7TR4q4BPtp8nO0s5o0Orlpf9jVO0xKvYNmD90JiwjkEpKK/NT8G4bEVEFo/NBELGt2EGlJXXn2iBTRa6IK1dDh/nY8N12FbTXN9mFPbXry8Ydn2BHCgssuyYku4+Di+s1/+vV3/mvLmmhXraHWzMHcBATRlCcAJZ3yIaADMFB1vkTuEzFt6Fw8ufa8vBEX38/fncPieow4PI9px4tZty7Oe3bS/OnD119U/SZmRxVy3cH1Ji7n6NkeGhOJ8bJc46iU7hkQbigZERHIIUQV15qI8tyyzsFfvUPiDTrOmjOdTFSqrxgppMRAZkN5f6dhxOkcMsc3culSf6Lj/Bfbdx6o8/QmZdzVZ1ZzXtqo000YzsGzkte9/tbWN59LCnIcmrBVD5helEJMTT0CUNKp5/NxLG6vr+faG5ZeiMaqgtHPiWqqW+QKUWXlcJ1R9vUx2CGzXYqOlDnMCbaiGdSUYT24ND68FtY4Z5Zqn6FZW9PVsp7RUisrqDRMJbA9A/31tc2KCGARbeU52nX2+uwyba4/mW9PeIXE6/vPjNEKacNoISXvXC+p1xhjnhe6yI8p0wqjWm23IMqd3lt54sN9F5okZF36y5of+ehLb25997UNKxN81a1V+WcP/utvZ2oNNjGYg6kCCKIpTwBKOuVDwCSAPtXA4Hznbfgwop5dyE778kSVur3dYVGSr+HxfqWp45TVJk8Haam8KdImPPV29RBjvlMqLawyJMfbewfp1ttjZvhbEy3lOfpBc3tWKam1tIGBfsIjJFaX4mlnzRggGsqzTYwYhYU3h8baHC/nzuxybYmApFmuRHPuyULDSJoTvGjF81ve2bwq1oMrb85L+fIf23Z8deBkRmXHsJGzmmwTFwhoCUBJEQdDBHrlg/InVdr4mDp6eQwsTlhM98mv0rTrOB4hwS7DZkmtWQZRVAxNq5KbmzicMUmYLl7MoktlfYSNoz1t7HZ8SVG1dtDZ09Ymd54xN5Cwig8PoBPCG1cNC+zSrDJy6cjamhxcuoXGuhIMPrP4q917UnNMyJxj0vLY4TuZvELjtdtKo+eG2xGNZZmGEXHA0hdXPxwlcCJ6eno687/78lRuo6k8BI36TnbqI8KmAgEo6VTw8p3aWNagPYlkoKuLZu/i4T/4Kj228LAsSrbq4tFinZxEJUbLL10ayjTtV4w+uW5AJmrrVMjlY5Iw6SzBdEZhgbifYHNH7bTX1tyWVUYOOm1dXTmErYefx0OhvuSbe2nGkObKcyr0eQKqXo4gxmfO47/b/Pso9djDSQnC9+GZbkRfWVqu9iRU3TUtJMaRHj8zkEHUllwe3AngsDB5Ll//nwKz6ewnJ2vG08u+ced975Q4npssBKCkk8WTv4YdAzeb2tVqKx6PnG60dzCxgM1kamc/dYNKMmGJlERNe4l2TtEqftMK35rci3JT+UMicYdcLle21TXRnEwIpa5Cr/lr/OpPpWQLTR0R1VVQafiuiUvoutnkR/dqy64Mf3OX5+qllCGq7/RfnyAgVOIWUzlYYXNCeURrTuqFlIvG/VNukYuSvJ0JeUlO1qDE090dbAx2CGsKR4OlGeeCCZXJKYxfwxOow9IIQEktzWO/Tn9Z/KDoecmPPr5i1SML5y9ImOXvpFuRFl0padHlQA0oxLyotcGjXsRJjSWl0N5RJe1RkQlL5F1Fu+4RJoMhKy9Sz/RSGwacSoXxdbhToSJPeurtUjr4uEwbmeU0ZAyD6Ra1ZlmYzdgjmMlnJPmVhrlSR0dHQl1dMmp3kexquW7HqcDRsd+GnOBtrM43wWmajztHcSNDezR/0ZXrnYNP2IfPnc7pKM4sNZTgC6bZDf676O7STiyMvGzZYzK9uKEL1ywM52Lv6K8TnBZZC5TUIt12r51mCRZs/H/vbv2vd19fP8ddJWoVi9vbmoUdhNusx57ZtCY2bvHjzt3kZzdUHcJ2hr3bjISHRi7Aa9rbSWWRct28bQdTN2lc7RsxfXagU01JcVFRg7FjNJoxubNHplB3lYt40x1VntFLyDTPEZdn8ovztL8pleRij5sg3KTUSgqMUko+ebNoRL69tjrFFf1n+vr6tDO9teVZpgj5uDl1XM+4Tt6iRT4U4WB4RK5UthdfGRrDyhTGCVY7n+BR08WOD62dO7jNlPwPhK1blmNGxc+LmLd27YitA/fqIpSzTAJQUsv02z302i3p5Xffej7O+treD/77gw//feinzIK8zIyMvLLKooyfjx/Y+/Xx7KupR44fP3G5tE5u78WVlpw6kTk6KdQ14cU33np6NqlCZMLogEbNCkomU1BnB3q3NVRZW/N5tkNZUENpl9knPjleqWAoGUwGP/bZ3ywU6PLZmXzXaRGrN5Hn3rcLW8hcKu3EATNodgKfO2b9nhws51cadpTKKvLHvHGTg+grP2dL1D18N1/yRT3bpJDybNjkzivd2NWBr24vaR5cX+qWFhZndA4R7W5oM+ZiOc55ckOUk17dme7ekcs3LnZSGk9w8YhaTC5+EcrWDvInK5p2kI5rihLAF/GmiONnbnhrdXDP1c93nDH1KY9REDxnRGpuFAoNU5HBa95cP10tqs5rdEyIdu9rLWyWWjc0diorL2QJ7SIWJ4b5B3n0lVSUlaZzk99Y4KHTE2X5938/XGSolzVn4x8fI1OXhl8qlYrRX5Oy6/t86/m/f2Xu4J6A1vRLPQkLppUe/vCYLj3JeLks2fxqPPmQNH/fRydrTHkt+pl3E60uHj2WUW96v3/YE//5UOv23brTABgslpqd8NIb88jxZe/1b7YdrxheIyf2mdeXBLJ1AkpuDu2ztTWIu7Lh7Bd7RIlvbpgxWu7bruz8PFV0y32mUyTULNFMnE9qiV4zR5/jooJZHbkn7kRGye41FQ/JKOEUGxfIpbFsXUMj3RWt5Sl7Pjtx8NB3aWmpWVqpdSFazlyXdNfmX72UXSOVK62Ifl3SU79y+HfpFDmH9vxSKTWugUtKcmq7xaUp+77N7ZCTc7KSTll3p7itubG2rrU09+KVrBLDEpMRVntBpXbOUnLjmkkZJW/lZRw8dmA8GSXvk7MM/eTsrf3MmIWxicGuTsz6skbSAlFR+ggZJZ+UZx/cdbJcn2VFM8ioRt6Y/tW2PRliovzMLxUj5nNV3eUp30BGzRHYE6ZNjEknjCvua0fiNm2d1fDx5+dvdciRiQ64hQQzlIGrno5xkN648P0PVxpMpdsTsc89b31obwapSmQzC9zk5PoS+XEO09+vp7E4XCZLo+jsvc1Ze/cBx9xNmzRfFwa8M79r3972+BeTuFn/e9HhcbfzP2aP0xdrlr2rfyBPVlPd0NE3ZrhJZ9vzuAx1X1enDGml98FdD7JKjEkfJG1Lbiu3tJofNNvUZ0JMW8USLP7d21u3/v7JDc8vY1761/sf/OvIMBl1dnbSqqXhsrLSqIxJSfobanmv4dSlkQ2oFfKebnPIKNmNopoWrn1FXlr29RapFZfH9l36WkjBuDKqHVgrpE1leaV1JmSUvDvQJ5VIyNE0ZNSS/2X8Wn3HitOvRXJi1zOQs39vdfDmt15dHcm/nc/5XrHrXlkf0pG554vt29//YPv3xaNFUSyWkBmiwyz2jVmqPVfJRZuIqr36yvNzJh4QWUaby5OJiqyselW4/pxnts2d/+cy8exBjyYQAbzdTyBn3P+usHzmr1sZomoe8PRliZukvVJRZ2P25XKZPnnIeDGZ1krlbbeU2wbPi+eL8rLKAp/dOlu489+pIvLl/hFfRaeoJvvrI5mjvvh0/427kxYYgate2zBd3UM48sihs/DCh7vSTGaw3kldeGbyEKD+dg8lnTzRcFeW0Lhu/oGOqs4uqcLTn5ubO94yzjiVesx6JDkpzk+3Zamrq6Xxl8+PlhL8xa9ujudrrFov3/2M7F11nuLDno9u+S25+36gKuWDA7n4gAhFmpOiOHUlvd2b3qTABCPGElDLWiuLbtTWN0ta71pGydqENUqOYecnj8fXnnjMT3hslhNhNdB49tDdLmw9UAf5rVivO8SkqzAdMvpAyU/qxqCkk9q998+4AeMZnmQbGsc5W97dnOzHHRBe2LUnY7zjnO9fb+64Ziv/lau8ldp0qrbijJEfVrnjOvAgCIwlACVFVNwLAd5s/VGhZKZ8bYmwn+/uoBTmHv3477vSDBvk76XW+17GPnGxX2VRE7lxXiFuGf1NgPveOhqYxAQwTzqJnXufTWPy3W07WiSWlAQUsXoN4xdRzJ+SPMRlKafPXKuSYpr0PkeJZVSPeVLL8NPk7KVSZFkySp5ixe9syvdzd5LLWoRNjKinn4wdOi/FKfGlv2wlz3b502+XBuI7d5MzYu+nVXi7v590UffEItAtkcgIGw6bM9BamJF19NjVduMnVpih/h50ovH8ti9ynFa+9OjoE6smlh3ozcQjACWdeD5Bj+4XAY3axc2PZqWQ1taTR0IxBG7OxjRaZebJo+dOnslUSAu/OS+eNt30kdT3q2Oo1+IJQEkt3oUw4M4JXM9oCJzBZ9k72fIDgsLFwryhDfdqUcnl/CbdpG9rh4xt4mS/O28GT049AlDSqefzqWyxvDw1lzzCimVHF94srKk3fQieg61GajgNdSrDgu13QQBKehew8OhkIJBfUa9WK3pMn2GqNdA/UCMssKSMhMngFYu3AUpq8S6EAXdJIDetgBUcY+J7f9p62DNWz+25nI7N+HcJdco/DiWd8iEw9QDUnTrVNOOZp+P97EZ+LoTus+SVP8R3/Hz+Dj4rMPWoweJbEkBmPgJkShKgC5a9+lyMk+47qnJxq7C2nTEjwrHm5JdHCk0frDolKU0Zo6ln5kNJp0ywwNAxBFj8wLAAVw7R21wpUttI6sb5ABTITXoC1JUUb/eTPkhg4LgEFKLK/KtXrlwtrBE3QUYRKFQIQEmp0ENZEAABENASgJIiDkAABECAKgEoKVWCKA8CIAACUFLEAAiAAAhQJQAlpUoQ5UEABEAASooYAAEQAAGqBKCkVAmiPAiAAAhASREDIAACIECVAJSUKkGUBwEQAAEoKWIABEAABKgSgJJSJYjyIAACIAAlRQyAAAiAAFUCUFKqBFEeBEAABKCkiAEQAAEQoEoASkqVIMqDAAiAAJQUMQACIAACVAlASakSRHkQAAEQgJIiBkAABECAKgEoKVWCKA8CIAACUFLEAAiAAAhQJQAlpUoQ5UEABEAASooYAAEQAAGqBKCkVAmiPAiAAAhASREDIAACIECVAJSUKkGUBwEQAAEoKWIABEAABKgSgJJSJYjyIAACIAAlRQyAAAiAAFUCUFKqBFEeBEAABKCkiAEQAAEQoEoASkqVIMqDAAiAAJQUMQACIAACVAlASakSRHkQAAEQgJIiBkAABECAKgEoKVWCKA8CIAACUFLEAAiAAAhQJQAlpUoQ5UEABEAASooYAAEQAAGqBKCkVAmiPAiAAAhASREDIAACIECVAJSUKkGUBwEQAAEoKWIABEAABKgSgJJSJYjyIAACIAAlRQyAAAiAAFUCUFKqBFEeBEAABKCkiAEQAAEQoEoASkqVIMqDAAiAAJQUMQACIAACVAlASakSRHkQAAEQgJIiBkAABECAKgEoKVWCKA8CIAACUFLEAAiAAAhQJQAlpUoQ5UEABEAASooYAAEQAAGqBKCkVAmiPAiAAAhASREDIAACIECVAJSUKkGUBwEQAAEoKWIABEAABKgSgJJSJYjyIAACIAAlRQyAAAiAAFUCUFKqBFEeBEAABKCkiAEQAAEQoErg/wOG4SyAGa9nYAAAAABJRU5ErkJggg=="/></p></div></div><p class="P1"><span class="T1">Binnekort meer informatie</span></p><p class="Standard">Â </p></body></html>

```

---

### Post by cdenley on 2010-03-16
I'm assuming the output from the second command was simply pasted incorrectly, and the command was correct when you ran it.

```

ls -l /var/www/edi-factuur.com
ls -l /var/www/haarenik.nl
grep -A 10 "<VirtualHost" /etc/apache2/apache2.conf /etc/apache2/mods-enabled/*.load /etc/apache2/mods-enabled/*.conf /etc/apache2/httpd.conf /etc/apache2/ports.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*

```

---

### Post by ragit on 2010-03-16
```

root@ip13-241:/home/ragit# ls -l /var/www/edi-factuur.com
ls -l /var/www/haarenik.nl
grep -A 10 "<VirtualHost" /etc/apache2/apache2.conf /etc/apache2/mods-enabled/*.load /etc/apache2/mods-enabled/*.conf /etc/apache2/httpd.conf /etc/apache2/ports.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*totaal 72
drwxr-xr-x 4 ftpuser ftpgroup 4096 2010-02-24 16:25 contact
drwxr-xr-x 3 ftpuser ftpgroup 4096 2010-01-26 16:32 demo
drwxr-xr-x 3 ftpuser ftpgroup 4096 2010-02-24 14:18 edi_mogelijkheden
-rw-r--r-- 1 ftpuser ftpgroup   53 2010-02-24 16:01 google89bff51c1ad650fb.html
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-01-26 17:57 images
-rw-r--r-- 1 ftpuser ftpgroup 4907 2010-02-24 16:01 index.html
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-01-26 16:32 information_links
drwxr-xr-x 3 ftpuser ftpgroup 4096 2010-01-26 23:59 investering
-rw-r--r-- 1 ftpuser ftpgroup 3148 2010-02-24 16:01 master.dwt
drwxr-xr-x 3 ftpuser ftpgroup 4096 2010-01-26 16:32 nieuws
drwxr-xr-x 3 ftpuser ftpgroup 4096 2010-01-26 16:32 oplossingen
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-01-26 16:32 over_ons
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-03-10 14:22 persoonlijk
-rw-r--r-- 1 ftpuser ftpgroup   24 2010-02-24 16:01 robots.txt
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-01-26 16:32 site_map
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-01-26 16:32 styles
drwxr-xr-x 3 ftpuser ftpgroup 4096 2010-01-26 16:32 visie
root@ip13-241:/home/ragit# ls -l /var/www/haarenik.nl
totaal 152
drwxr-xr-x 3 ftpuser ftpgroup  4096 2010-01-07 11:37 about_me
drwxr-xr-x 3 ftpuser ftpgroup  4096 2010-01-07 11:37 contact
-rw-r--r-- 1 ftpuser ftpgroup    53 2010-02-09 18:57 google89bff51c1ad650fb.html
drwxr-xr-x 2 ftpuser ftpgroup  4096 2010-01-25 15:01 images
-rw-r--r-- 1 ftpuser ftpgroup 19074 2010-02-09 18:57 img34.jpg
-rw-r--r-- 1 ftpuser ftpgroup  6067 2010-02-09 18:57 imgB.gif
-rw-r--r-- 1 ftpuser ftpgroup  4332 2010-02-09 18:57 index.html
drwxr-xr-x 2 ftpuser ftpgroup  4096 2010-01-07 11:38 links
-rw-r--r-- 1 ftpuser ftpgroup  2053 2010-02-09 18:57 master.dwt
-rw-r--r-- 1 ftpuser ftpgroup 49320 2010-02-09 18:57 naamloos.JPG
drwxr-xr-x 2 ftpuser ftpgroup  4096 2010-01-31 19:47 photo_gallery
drwxr-xr-x 3 ftpuser ftpgroup  4096 2010-01-25 15:02 Prijslijst
drwxr-xr-x 7 ftpuser ftpgroup  4096 2010-03-13 19:14 prive
drwxr-xr-x 2 ftpuser ftpgroup  4096 2010-01-07 11:38 resume
-rw-r--r-- 1 ftpuser ftpgroup    24 2010-02-09 18:57 robots.txt
drwxr-xr-x 3 ftpuser ftpgroup  4096 2010-01-25 23:02 stage
drwxr-xr-x 2 ftpuser ftpgroup  4096 2010-01-07 11:38 styles
-rw-r--r-- 1 ftpuser ftpgroup  9216 2010-02-09 18:57 zzp.xls

```
```

root@ip13-241:/home/ragit# grep -A 10 "<VirtualHost" /etc/apache2/apache2.conf /etc/apache2/mods-enabled/*.load /etc/apache2/mods-enabled/*.conf /etc/apache2/httpd.conf /etc/apache2/ports.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*
/etc/apache2/apache2.conf:# If you do not specify an ErrorLog directive within a <VirtualHost>
/etc/apache2/apache2.conf-# container, error messages relating to that virtual host will be
/etc/apache2/apache2.conf:# logged here.  If you *do* define an error logfile for a <VirtualHost>
/etc/apache2/apache2.conf-# container, that host's errors will be logged there and not here.
/etc/apache2/apache2.conf-#
/etc/apache2/apache2.conf-ErrorLog /var/log/apache2/error.log
/etc/apache2/apache2.conf-
/etc/apache2/apache2.conf-#
/etc/apache2/apache2.conf-# LogLevel: Control the number of messages logged to the error_log.
/etc/apache2/apache2.conf-# Possible values include: debug, info, notice, warn, error, crit,
/etc/apache2/apache2.conf-# alert, emerg.
/etc/apache2/apache2.conf-#
/etc/apache2/apache2.conf-LogLevel warn
--
/etc/apache2/conf.d/squirrelmail.conf:#<VirtualHost 1.2.3.4>
/etc/apache2/conf.d/squirrelmail.conf-#  DocumentRoot /usr/share/squirrelmail
/etc/apache2/conf.d/squirrelmail.conf-#  ServerName webmail.example.com
/etc/apache2/conf.d/squirrelmail.conf-#</VirtualHost>
/etc/apache2/conf.d/squirrelmail.conf-
/etc/apache2/conf.d/squirrelmail.conf-# redirect to https when available (thanks omen@descolada.dartmouth.edu)
/etc/apache2/conf.d/squirrelmail.conf-#
/etc/apache2/conf.d/squirrelmail.conf-#  Note: There are multiple ways to do this, and which one is suitable for
/etc/apache2/conf.d/squirrelmail.conf-#  your site's configuration depends. Consult the apache documentation if
/etc/apache2/conf.d/squirrelmail.conf-#  you're unsure, as this example might not work everywhere.
/etc/apache2/conf.d/squirrelmail.conf-#
--
/etc/apache2/sites-enabled/default-ssl:<VirtualHost _default_:443>
/etc/apache2/sites-enabled/default-ssl- ServerAdmin webmaster@localhost
/etc/apache2/sites-enabled/default-ssl-
/etc/apache2/sites-enabled/default-ssl- DocumentRoot /var/www
/etc/apache2/sites-enabled/default-ssl- <Directory />
/etc/apache2/sites-enabled/default-ssl-         Options FollowSymLinks
/etc/apache2/sites-enabled/default-ssl-         AllowOverride None
/etc/apache2/sites-enabled/default-ssl- </Directory>
/etc/apache2/sites-enabled/default-ssl- <Directory /var/www/>
/etc/apache2/sites-enabled/default-ssl-         Options Indexes FollowSymLinks MultiViews
/etc/apache2/sites-enabled/default-ssl-         AllowOverride None
--
/etc/apache2/sites-enabled/djuwya.nl.conf:<VirtualHost *>
/etc/apache2/sites-enabled/djuwya.nl.conf-ServerAlias djuwya.nl *.djuwya.nl
/etc/apache2/sites-enabled/djuwya.nl.conf-DocumentRoot /var/www/djuwya.nl
/etc/apache2/sites-enabled/djuwya.nl.conf-ServerName djuwya.nl
/etc/apache2/sites-enabled/djuwya.nl.conf-<Directory "/var/www/djuwya.nl">
/etc/apache2/sites-enabled/djuwya.nl.conf-allow from all
/etc/apache2/sites-enabled/djuwya.nl.conf-Options +Indexes
/etc/apache2/sites-enabled/djuwya.nl.conf-</Directory>
/etc/apache2/sites-enabled/djuwya.nl.conf-</VirtualHost>

```

strange that in de second command only djuwya shows up.....

how is this to fix?

---

### Post by cdenley on 2010-03-16
> **ragit said:**
> 
strange that in de second command only djuwya shows up.....


Not very strange considering how apache is behaving. Post the actual content of the files you expected to show up, since apparently they don't match what you first posted.

---

### Post by ragit on 2010-03-16
/var/www/edi-factuur.com/index.html
/var/www/haarenik.nl/index.html
/var/www/djuwya.nl/index.html

---

### Post by cdenley on 2010-03-16
> **ragit said:**
> /var/www/edi-factuur.com/index.html
/var/www/haarenik.nl/index.html
/var/www/djuwya.nl/index.html

That is the content of the vhost configuration files you expected to show up after running the "grep" command?
```

cat /etc/apache2/sites-available/djuwya.nl.conf
cat /etc/apache2/sites-available/edi-factuur.com.conf
cat /etc/apache2/sites-available/haarenik.nl.conf

```

---

### Post by ragit on 2010-03-18
<VirtualHost edi-factuur.com>
DocumentRoot /var/www/edi-factuur.com
ServerName edi-factuur.com
*ServerAlias* *edi-factuur.nl edi-factuur.com
<Directory "/var/www/edi-factuur.com">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost haarenik.nl>
DocumentRoot "/var/www/haarenik.nl"
ServerName haarenik.nl
*ServerAlias* *haarenik.nl
<Directory "/var/www/haarenik.nl">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost djuwya.nl>
DocumentRoot "/var/www/djuwya.nl"
ServerName djuwya.nl
*ServerAlias* *djuwya.nl
<Directory "/var/www/djuwya.nl">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

---

### Post by cdenley on 2010-03-18
As I suspected, that does NOT match the configuration you originally posted! These corrections should fix it, I believe.

```
<VirtualHost **[COLOR="Red"]*:80[/COLOR]**>
DocumentRoot /var/www/edi-factuur.com
ServerName edi-factuur.com
ServerAlias [COLOR="Red"]***.edi-factuur.nl**[/COLOR]
<Directory "/var/www/edi-factuur.com">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost **[COLOR="Red"]*:80[/COLOR]**>
DocumentRoot "/var/www/haarenik.nl"
ServerName haarenik.nl
ServerAlias [COLOR="Red"]***.haarenik.nl**[/COLOR]
<Directory "/var/www/haarenik.nl">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost **[COLOR="Red"]*:80[/COLOR]**>
DocumentRoot "/var/www/djuwya.nl"
ServerName djuwya.nl
ServerAlias [COLOR="Red"]***.djuwya.nl**[/COLOR]
<Directory "/var/www/djuwya.nl">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

---

### Post by ragit on 2010-03-21
thankyou, problem solved!

---

