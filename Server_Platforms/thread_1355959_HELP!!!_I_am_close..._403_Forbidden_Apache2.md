---
title: "HELP!!! I am close... 403 Forbidden Apache2"
date: 2009-12-15
forum: Server Platforms
---

### Post by larson15 on 2009-12-15
I am trying to install a program called Flickrframe to make a digital picture frame.  I am following online instructions , however I have seem to gotten hung up.  I am trying to connect to a website from another computer by going ipaddress/authwizard.pl  I am new to Ubuntu so please work with me.  Thanks.  I have edited the apache2/mods-enabled/mime.conf to add the AddHandler cgi-script .pl and removed the hash above that file.  Here are the files I changed.  I might have done something wrong.  Ask me if you have any questions.  Then I edited the /etc/apache2/sites-enabled/000-default to

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/amber/flickrframe/htdocs
    <Directory />
        Options FollowSymLinks +ExecCGI
        AllowOverride None
    </Directory>
    <Directory /home/amber/flickrframe/htdocs>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
[B]
/etc/apache2/mods-enabled/mime.conf[/B]

<IfModule mod_mime.c>

#
# TypesConfig points to the file containing the list of mappings from
# filename extension to MIME-type.
#
TypesConfig /etc/mime.types

#
# AddType allows you to add to or override the MIME configuration
# file mime.types for specific file types.
#
#AddType application/x-gzip .tgz
#
# AddEncoding allows you to have certain browsers uncompress
# information on the fly. Note: Not all browsers support this.
# Despite the name similarity, the following Add* directives have
# nothing to do with the FancyIndexing customization directives above.
#
#AddEncoding x-compress .Z
#AddEncoding x-gzip .gz .tgz
#AddEncoding x-bzip2 .bz2
#
# If the AddEncoding directives above are commented-out, then you
# probably should define those extensions to indicate media types:
#
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz
AddType application/x-bzip2 .bz2

#
# DefaultLanguage and AddLanguage allows you to specify the language of 
# a document. You can then use content negotiation to give a browser a 
# file in a language the user can understand.
#
# Specify a default language. This means that all data
# going out without a specific language tag (see below) will 
# be marked with this one. You probably do NOT want to set
# this unless you are sure it is correct for all cases.
#
# * It is generally better to not mark a page as 
# * being a certain language than marking it with the wrong
# * language!
#
# DefaultLanguage nl
#
# Note 1: The suffix does not have to be the same as the language
# keyword --- those with documents in Polish (whose net-standard
# language code is pl) may wish to use "AddLanguage pl .po" to
# avoid the ambiguity with the common suffix for perl scripts.
#
# Note 2: The example entries below illustrate that in some cases 
# the two character 'Language' abbreviation is not identical to 
# the two character 'Country' code for its country,
# E.g. 'Danmark/dk' versus 'Danish/da'.
#
# Note 3: In the case of 'ltz' we violate the RFC by using a three char
# specifier. There is 'work in progress' to fix this and get
# the reference data for rfc1766 cleaned up.
#
# Catalan (ca) - Croatian (hr) - Czech (cs) - Danish (da) - Dutch (nl)
# English (en) - Esperanto (eo) - Estonian (et) - French (fr) - German (de)
# Greek-Modern (el) - Hebrew (he) - Italian (it) - Japanese (ja)
# Korean (ko) - Luxembourgeois* (ltz) - Norwegian Nynorsk (nn)
# Norwegian (no) - Polish (pl) - Portugese (pt)
# Brazilian Portuguese (pt-BR) - Russian (ru) - Swedish (sv)
# Simplified Chinese (zh-CN) - Spanish (es) - Traditional Chinese (zh-TW)
#
AddLanguage ca .ca
AddLanguage cs .cz .cs
AddLanguage da .dk
AddLanguage de .de
AddLanguage el .el
AddLanguage en .en
AddLanguage eo .eo
# See README.Debian for Spanish
AddLanguage es .es
AddLanguage et .et
AddLanguage fr .fr
AddLanguage he .he
AddLanguage hr .hr
AddLanguage it .it
AddLanguage ja .ja
AddLanguage ko .ko
AddLanguage ltz .ltz
AddLanguage nl .nl
AddLanguage nn .nn
AddLanguage no .no
AddLanguage pl .po
AddLanguage pt .pt
AddLanguage pt-BR .pt-br
AddLanguage ru .ru
AddLanguage sv .sv
# See README.Debian for Turkish
AddLanguage tr .tr
AddLanguage zh-CN .zh-cn
AddLanguage zh-TW .zh-tw

#
# Commonly used filename extensions to character sets. You probably
# want to avoid clashes with the language extensions, unless you
# are good at carefully testing your setup after each change.
# See [http://www.iana.org/assignments/character-sets](http://www.iana.org/assignments/character-sets) for the
# official list of charset names and their respective RFCs.
#
AddCharset us-ascii    .ascii .us-ascii
AddCharset ISO-8859-1  .iso8859-1  .latin1
AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
AddCharset ISO-8859-3  .iso8859-3  .latin3
AddCharset ISO-8859-4  .iso8859-4  .latin4
AddCharset ISO-8859-5  .iso8859-5  .cyr .iso-ru
AddCharset ISO-8859-6  .iso8859-6  .arb .arabic
AddCharset ISO-8859-7  .iso8859-7  .grk .greek
AddCharset ISO-8859-8  .iso8859-8  .heb .hebrew
AddCharset ISO-8859-9  .iso8859-9  .latin5 .trk
AddCharset ISO-8859-10  .iso8859-10  .latin6
AddCharset ISO-8859-13  .iso8859-13
AddCharset ISO-8859-14  .iso8859-14  .latin8
AddCharset ISO-8859-15  .iso8859-15  .latin9
AddCharset ISO-8859-16  .iso8859-16  .latin10
AddCharset ISO-2022-JP .iso2022-jp .jis
AddCharset ISO-2022-KR .iso2022-kr .kis
AddCharset ISO-2022-CN .iso2022-cn .cis
AddCharset Big5        .Big5       .big5 .b5
AddCharset cn-Big5     .cn-big5
# For russian, more than one charset is used (depends on client, mostly):
AddCharset WINDOWS-1251 .cp-1251   .win-1251
AddCharset CP866       .cp866
AddCharset KOI8      .koi8
AddCharset KOI8-E      .koi8-e
AddCharset KOI8-r      .koi8-r .koi8-ru
AddCharset KOI8-U      .koi8-u
AddCharset KOI8-ru     .koi8-uk .ua
AddCharset ISO-10646-UCS-2 .ucs2
AddCharset ISO-10646-UCS-4 .ucs4
AddCharset UTF-7       .utf7
AddCharset UTF-8       .utf8
AddCharset UTF-16      .utf16
AddCharset UTF-16BE    .utf16be
AddCharset UTF-16LE    .utf16le
AddCharset UTF-32      .utf32
AddCharset UTF-32BE    .utf32be
AddCharset UTF-32LE    .utf32le
AddCharset euc-cn      .euc-cn
AddCharset euc-gb      .euc-gb
AddCharset euc-jp      .euc-jp
AddCharset euc-kr      .euc-kr
#Not sure how euc-tw got in - IANA doesn't list it???
AddCharset EUC-TW      .euc-tw
AddCharset gb2312      .gb2312 .gb
AddCharset iso-10646-ucs-2 .ucs-2 .iso-10646-ucs-2
AddCharset iso-10646-ucs-4 .ucs-4 .iso-10646-ucs-4
AddCharset shift_jis   .shift_jis .sjis

#
# AddHandler allows you to map certain file extensions to "handlers":
# actions unrelated to filetype. These can be either built into the server
# or added with the Action directive (see below)
#
# To use CGI scripts outside of ScriptAliased directories:
# (You will also need to add "ExecCGI" to the "Options" directive.)
#
AddHandler cgi-script .cgi
AddHandler cgi-script .pl
#
# For files that include their own HTTP headers:
#
#AddHandler send-as-is asis

#
# For server-parsed imagemap files:
#
#AddHandler imap-file map

#
# For type maps (negotiated resources):
# (This is enabled by default to allow the Apache "It Worked" page
#  to be distributed in multiple languages.)
#
AddHandler type-map var

#
# Filters allow you to process content before it is sent to the client.
#
# To parse .shtml files for server-side includes (SSI):
# (You will also need to add "Includes" to the "Options" directive.)
#
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml

</IfModule>

**The weird thing is that if i change the authwizard.pl file from .pl to html the site works but when you continue to the next page it disconnects.  Any help would be so great.  Thanks**

---

### Post by cariboo on 2009-12-15
What does the error log tell you? Check in /var/log/apache2.

---

### Post by northern lights on 2009-12-15
If changing the file extension to html really does the trick (did you access it by double-clicking the file or via [http://localhost?](http://localhost?) If you double-clicked it it wasn't loaded via apache), permissions are probably not it, still do others (not you, not users within your group) have access rights to */home/amber/flickrframe* and all its contents?

---

### Post by larson15 on 2009-12-15
cariboo907 - here is what the error log says...

[Tue Dec 15 21:41:46 2009] [notice] caught SIGTERM, shutting down
[Tue Dec 15 21:41:51 2009] [notice] Apache/2.2.12 (Ubuntu) configured -- resuming normal operations
[Tue Dec 15 21:41:59 2009] [error] [client 192.168.15.6] Options ExecCGI is off in this directory: /home/amber/flickrframe/htdocs/authwizard.pl

When I restart apache2 the terminal says its running fine, then I type in the local ip address from another computer to try and access the site.  Am I doing that right?

Northern Lights - No, I accessed it through Firefox.  And there is only one user created called amber which has read and write permissions set for everything.

**Thanks for the replies guys!! Hope you have some insight**

---

### Post by larson15 on 2009-12-15
I figured it out after looking at the error log.  Thanks so much guys

---

