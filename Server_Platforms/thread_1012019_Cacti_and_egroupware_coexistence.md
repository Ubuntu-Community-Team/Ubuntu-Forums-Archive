---
title: "Cacti and egroupware coexistence"
date: 2008-12-15
forum: Server Platforms
---

### Post by el__es on 2008-12-15
Hello forums,

I have the cacti package : 

> 

cacti   0.8.7b-2ubuntu1



and egroupware :

> 
  1.2.107-2.dfsg-2ubuntu1



This however leads to a weird result :

> Warning: mb_ereg_replace() [function.mb-ereg-replace]: mbregex compile err: premature end of char-class in /usr/share/cacti/site/include/global.php on line 86

Warning: mb_ereg_replace() [function.mb-ereg-replace]: mbregex compile err: premature end of char-class in /usr/share/cacti/site/include/global.php on line 87

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/cacti/site/include/global.php:86) in /usr/share/cacti/site/include/global.php on line 121

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/cacti/site/include/global.php:86) in /usr/share/cacti/site/include/global.php on line 122

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/cacti/site/include/global.php:86) in /usr/share/cacti/site/include/global.php on line 123

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/cacti/site/include/global.php:86) in /usr/share/cacti/site/include/global.php on line 124

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/cacti/site/include/global.php:86) in /usr/share/cacti/site/include/global.php on line 125

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /usr/share/cacti/site/include/global.php:86) in /usr/share/cacti/site/include/global.php on line 129

Warning: include(/database.php) [function.include]: failed to open stream: No such file or directory in /usr/share/cacti/site/include/global.php on line 184

Warning: include() [function.include]: Failed opening '/database.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/cacti/site/include/global.php on line 184

Warning: include_once(/functions.php) [function.include-once]: failed to open stream: No such file or directory in /usr/share/cacti/site/include/global.php on line 185

Warning: include_once() [function.include]: Failed opening '/functions.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/cacti/site/include/global.php on line 185

Fatal error: Call to undefined function db_connect_real() in /usr/share/cacti/site/include/global.php on line 191

displayed if I try to use cacti frontend (the snmp/rrdtool seems to be fine however, no corruption spotted) simultaneously (on the same computer - whether it is different tabs or different FF windows, doesnt matter)
Usually happens if some activity was performed on egroupware (session timeout ? I don't think so...)

What could possibly be the problem ?

---

### Post by el__es on 2008-12-16
I went to /var/log/apache2/error log and seen this :


> [Tue Dec 16 15:42:15 2008] [error] [client 192.168.1.41] PHP Warning:  mb_strstr() [<a href='function.mb-strstr'>function.mb-strs
tr</a>]: Empty delimiter. in /usr/share/egroupware/phpgwapi/inc/class.html.inc.php on line 117, referer: [http://office-desktop/eg](http://office-desktop/eg)
roupware/infolog/index.php
[Tue Dec 16 15:42:45 2008] [error] [client 192.168.1.41] PHP Warning:  mb_strstr() [<a href='function.mb-strstr'>function.mb-strs
tr</a>]: Empty delimiter. in /usr/share/egroupware/phpgwapi/inc/class.html.inc.php on line 117, referer: [http://office-desktop/eg](http://office-desktop/eg)
roupware/index.php?menuaction=infolog.uicustomfields.edit
[Tue Dec 16 15:43:11 2008] [error] [client 192.168.1.41] PHP Warning:  mb_strstr() [<a href='function.mb-strstr'>function.mb-strs
tr</a>]: Empty delimiter. in /usr/share/egroupware/phpgwapi/inc/class.html.inc.php on line 117, referer: [http://office-desktop/eg](http://office-desktop/eg)
roupware/etemplate/process_exec.php?menuaction=infolog.uicustomfields.edit
[Tue Dec 16 15:44:25 2008] [error] [client 192.168.1.41] PHP Warning:  mb_strstr() [<a href='function.mb-strstr'>function.mb-strs
tr</a>]: Empty delimiter. in /usr/share/egroupware/phpgwapi/inc/class.html.inc.php on line 117, referer: [http://office-desktop/eg](http://office-desktop/eg)
roupware/etemplate/process_exec.php?menuaction=infolog.uicustomfields.edit
[Tue Dec 16 16:47:39 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Dec 16 16:47:50 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch configured -- resuming normal o
perations

the line mentioned ( /usr/share/egroupware/phpgwapi/inc/class.html.inc.php line 117 ) is in function tooltip :

> function tooltip($text,$do_lang=False,$options=False)
        {
                if (!$this->wz_tooltip_included)
                {
LINE 117 >> if !strstr('wz_tooltip',$GLOBALS['egw_info']['flags']['need_footer']))
                        {
                                $GLOBALS['egw_info']['flags']['need_footer'] .= '<script language="JavaScript" type="text/javascript
" src="'.$this->phpgwapi_js_url.'/wz_tooltip/wz_tooltip.js"></script>'."\n";
                        }
                        $this->wz_tooltip_included = True;
                }



Does this make sense ?

---

### Post by el__es on 2008-12-17
[http://www.nabble.com/Cacti-and-egroupware-coexistence-td21030528s3741.html](http://www.nabble.com/Cacti-and-egroupware-coexistence-td21030528s3741.html)

For the record : if you have Cacti and egroupware on the same machine, go to

/etc/apache2/conf.d/egroupware  change line 29 from

- php_value mbstring.func_overload 7

to

+ php_value mbstring.func_overload 0

That made it.

---

