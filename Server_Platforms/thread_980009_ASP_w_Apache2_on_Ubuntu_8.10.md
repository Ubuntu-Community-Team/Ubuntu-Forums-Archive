---
title: "ASP w/ Apache2 on Ubuntu 8.10"
date: 2008-11-12
forum: Server Platforms
---

### Post by fackamato on 2008-11-12
I'm trying to get ASP support on Linux working. Using Ubuntu Intrepid 8.10 and Apache2.

This is the asp script that I'm trying to use:

*calendar.asp*

```
<%
dim thisDate

If Request.Querystring("EventDate") = "" then
    thisDate = FormatDateTime(now(),2)
else
    thisDate = Request.Querystring("EventDate")
end if
    
CurrentMonth = Month(thisDate)
CurrentMonthName = MonthName(CurrentMonth)
CurrentYear = Year(thisDate)

FirstDayDate = DateSerial(CurrentYear, CurrentMonth, 1)
FirstDay = WeekDay(FirstDayDate, 0)
CurrentDay = FirstDayDate
testCurrentDay = date
CurrentWeek = DatePart("ww",Request.querystring("EventDate"))

usDateFormat = ""& CurrentYear &"-"& CurrentMonth &"-"& Day(thisDate) &""

if not Request.Querystring("week") = "" then
    firstDayWeek = (dateadd( "d",(2-datepart("w",thisDate)),thisDate)-7)
    lastDayWeek = firstDayWeek + 6

    if Day(lastDayWeek) <  Day(firstDayWeek) then
        myMonth = CurrentMonth - 1
        myYear = CurrentYear
        if myMonth = 0 then
            myMonth = 12
            myYear = CurrentYear - 1
        end if
    else
        myMonth = CurrentMonth
        myYear = CurrentYear
    end if

    firsUsDateFormat = ""& myYear &"-"& myMonth &"-"& Day(firstDayWeek) &""
    endUsDateFormat = ""& CurrentYear &"-"& CurrentMonth &"-"& Day(lastDayWeek) &""
end if

if not Request.Querystring("month") = "" then

end if
%>
    <table cols="7" border="0" cellpadding="0" cellspacing="1">

    <tr>
        <td align="center" bgcolor="Teal" style="background: #3f7dcd;">
            <A Href="default.asp?EventDate=<%= Server.URLEncode(DateAdd("m",-1, thisDate))%><%=linkString%>"><</A>
        </td>
        <td colspan="5" align="center" bgcolor="Teal" style="background: #3f7dcd; color: white;">
            <b><%= CurrentYear %> - <%= CurrentMonthName %></b>
        </td>
        <td align="center" bgcolor="Teal" style="background: #3f7dcd;">
            <A Href="default.asp?EventDate=<%= Server.URLEncode(DateAdd("m",1,thisDate))%><%=linkString%>">></A>
        </td>
    </tr>
    <tr>
        <% For DayLoop = 1 to 5%>
            <td style="background: yellow; width: 30px;" align="center"><%= WeekDayName(Dayloop, True, 0)%></td>
        <% Next%>
        <td style="width: 30px; border: 0px;" align="center">&nbsp;</td>
        <td style="background: yellow; width: 30px;" align="center">W</td>
    </tr>
    <tr><%
        If FirstDay <> 1 Then
            if FirstDay = 7 then%>
                <td Colspan="6" style="border: 0px solid Black; background: #999999;">&nbsp;</td><%
            else%>
                <td Colspan="<%=FirstDay -1%>" style="border: 0px solid Black; background: #999999;">&nbsp;</td><%
            End if
        End if
        DayCounter = FirstDay
        CorrectMonth = True
        dim holderName, todayDate

        holderName = ""
        todayDate = "" 

        Do While CorrectMonth = True

            todayDate = ""& Day(CurrentDay) &"/"& CurrentMonth &"/"& CurrentYear &""            
            holderName = WeekdayName(Weekday(todayDate))

            'If CurrentDay = EventDate Then
            If testCurrentDay = CurrentDay AND NOT holderName = "Sunday" AND NOT holderName = "Saturday" then%>
                <td align="Center" style="background: red;"><A Href="default.asp?EventDate=<%= Server.URLEncode(CurrentDay)%><%=linkString%>"><%=Day(CurrentDay)%></A></td><%
            ElseIf holderName = "Saturday" then%>
                <td align="Center" style="border: 0px;">&nbsp;</td><%
            ElseIf holderName = "Sunday" then%>
                <td align="Center" style="background: #eaeaea;">
                        <A Href="default.asp?EventDate=<%= Server.URLEncode(CurrentDay)%><%=linkString%>&week=<%=DatePart("ww",todayDate)-1%>"><%=DatePart("ww",todayDate)-1%></A>
                </td><%
            Else%>
                <td align="Center" style="background: #eaeaea;"><A Href="default.asp?EventDate=<%= Server.URLEncode(CurrentDay)%><%=linkString%>"><%=Day(CurrentDay)%></A></td>
            <% End if%>            

            <%DayCounter = DayCounter + 1
            If DayCounter > 7 then
                DayCounter = 1%>
                </tr>
                <tr>
            <%End if

            CurrentDay = DateAdd("d", 1, CurrentDay)

            If Month(CurrentDay) <> CurrentMonth then
                CorrectMonth = False
            End if
            holder = ""
        Loop

        IF DayCounter <> 1 Then%>
            <td Colspan="<%=8-DayCounter%>" style="border: 0px solid Black; background: #999999;"> </td>
        <% End if%>
    </tr>
    </table>
```

*/etc/apache2/httpd.conf*

```
ServerName 9.161.60.108
 <Directory /home/kenneth/www/ >
    Options FollowSymLinks
    AllowOverride All
  </Directory>
AddHandler cgi-script .pl
```

*/etc/apache2/conf.d/kenneth.conf*

```
# kenneth idc
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/home/kenneth/www/cgi-bin/">
    AllowOverride None
    Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
     Allow from all
</Directory>
Alias /idc /home/kenneth/www

<Directory /home/kenneth/www>
        Options Indexes FollowSymLinks
        DirectoryIndex default.asp default.aspx index.php index.html index.htm
                AllowOverride All
                Order allow,deny
                Allow from all
#                SetHandler mono

        # Authorize for setup
        <IfModule mod_php4.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
</Directory>

<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.asp$">
Options +ExecCGI
</Files>
```

```
kenneth@asdf:/etc/apache2$ perl -v

This is perl, v5.10.0 built for i486-linux-gnu-thread-multi
```

*/var/log/apache2/access.log*

```
9.161.59.29 - - [12/Nov/2008:17:55:09 +0000] "GET /idc/calendar.asp HTTP/1.1" 200 18005 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; sv-SE; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3"
```

*/var/log/apache2/error.log*

```
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0100;0.0011] undefing sub Apache::ASP::__ASP__home_kenneth_www_calendar_aspx399322a5d013d9a909ebc17350480fc5xINC code CODE(0xb9994120)
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [error] error compiling calendar.asp: maybe use strict error: Bareword found where operator expected at /home/kenneth/www/calendar.asp line 4, near "If Request" <--> , /usr/local/share/perl/5.10.0/Apache/ASP.pm line 1466
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0107;0.0007] ASP Done Processing Apache::ASP=HASH(0xb95b7a08) - Application: Apache::ASP::Application=HASH(0xb99595e0); GlobalASA: Apache::ASP::GlobalASA=HASH(0xb95b77e8); Internal: Apache::ASP::State=HASH(0xb96fc318); Request: Apache::ASP::Request=HASH(0xb95d0f48); Response: Apache::ASP::Response=HASH(0xb998ccf8); Server: Apache::ASP::Server=HASH(0xb92ed370); Session: Apache::ASP::Session=HASH(0xb9948020); app_state: 1; basename: calendar.asp; cleanup: ARRAY(0xb92ed2d0); compile_checksum: 399322a5d013d9a909ebc17350480fc5; compile_error: 1; compile_eval: SCALAR(0xb96383a0); compile_includes: 1; compile_perl_count: 1; cookie_domain: ; cookie_path: /; dbg: 4; debugs_output: ARRAY(0xb92ed2e0); destroy: 1; dir_config: APR::Table=HASH(0xb92ed150); dirname: /home/kenneth/www/; errors_output: ARRAY(0xb998f920); errs: 1; filename: /home/kenneth/www/calendar.asp; global: /home/kenneth/www//.; global_package: Apache::ASP; group_refresh: 30; headers_in: APR::Table=HASH(0xb92ed170); includes_dir: ARRAY(0xb95b7a48); init_packages: ARRAY(0xb99946d0); inode_names: ; lang_comment: #; lang_language: PerlScript; lang_module: Apache::ASP::Lang::PerlScript; lang_object: Apache::ASP::Lang::PerlScript=HASH(0xb94c0348); last_time: 1226512510.0100; no_cache: ; package: Apache::ASP; paranoid_session: ; parse_config: 1; parse_file_count: 1; pod_comments: 1; r: Apache2::RequestRec=SCALAR(0xb92ed120); remote_ip: 9.161.59.29; request_binary_read: 1; search_dirs_cache: HASH(0xb92ed260); secure_session: ; session_cookie: 1; session_count: 1; session_id: 08de1e4b9722a63891db90effabd9efb; session_serialize: ; session_state: 1; session_timeout: 300; session_url: 1; session_url_force: ; session_url_match: ; session_url_parse: 0; session_url_parse_match: ; start_time: 1226512509.98789; stat_inc: 0; stat_inc_match: 0; stat_scripts: 1; state_db: ; state_dir: /tmp/asp; state_manager: 10; state_serialize: ; state_serializer: ; ua: Mozilla/5.0 (Windows; U; Windows NT 5.1; sv-SE; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3; use_strict: 1; win32: 0; xml_subs_match: my:\\w+; xml_subs_perl_args: 1; xml_subs_strict: ; xslt: ;
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0111;0.0004] errors out  <--> <li> error compiling calendar.asp: maybe use strict error: Bareword found where operator expected at /home/kenneth/www/calendar.asp line 4, near &quot;If Request&quot; <--> , /usr/local/share/perl/5.10.0/Apache/ASP.pm line 1466
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0199;0.0088] building headers
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0201;0.0002] sending cgi headers
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0208;0.0007] destroying ASP object Apache::ASP=HASH(0xb95b7a08)
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0210;0.0002] testing internal time for cleanup groups
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0217;0.0007] current_master - Checked: 1226512493; PID: 21159; ServerID: 919e63567bde4ffe;  - is_master - 0
[Wed Nov 12 17:55:10 2008] [error] [asp] [21509] [debug] [1226512510.0219;0.0002] 1226512510 time is fresh, is_master 0 - Checked: 1226512493; PID: 21159; ServerID: 919e63567bde4ffe;
```

*.htaccess*

```

PerlSetVar Global  .		
PerlSetVar GlobalPackage Apache::ASP
PerlSetVar StateDir  /tmp/asp
PerlSetVar StatINC 0
PerlSetVar StatINCMatch 0
PerlSetVar Clean 0
PerlSetVar DynamicIncludes 1
PerlSetVar FileUploadMax 50000
PerlSetVar FileUploadTemp 1
PerlSetVar SessionQueryParse 0
PerlSetVar SessionQuery 1
#PerlSetVar Debug 2
PerlSetVar Debug -4
PerlSetVar StateCache 0
PerlSetVar SessionCount 1
PerlSetVar TimeHiRes 1
PerlSetVar CompressGzip 0
PerlSetVar UseStrict 1
#PerlSetVar CacheDB DB_File
PerlSetVar CacheDB MLDBM::Sync::SDBM_File

# .asp files for Session state enabled
<Files ~ (\.asp)>
	SetHandler perl-script
	PerlHandler Apache::ASP
	PerlSetVar CookiePath  /	
	PerlSetVar SessionTimeout  5
	PerlSetVar RegisterIncludes 1
	PerlSetVar XMLSubsMatch my:\w+
	PerlSetVar AllowApplicationState 1
	PerlSetVar AllowSessionState 1
#	PerlSetVar StateSerializer Storable
#	PerlSetVar StateDB DB_File
#	PerlSetVar StatScripts 0
</Files>

# .htm files for the ASP parsing, but not the $Session object
# NoState turns off $Session & $Application
<Files ~ (\.htm)>
	SetHandler perl-script
	PerlHandler Apache::ASP
	PerlSetVar NoState 0 
	PerlSetVar BufferingOn 1
	PerlSetVar NoCache 0
	PerlSetVar DebugBufferLength 500
</Files>

<Files ~ (\.xml)>
	SetHandler perl-script
	PerlHandler Apache::ASP
	PerlSetVar NoState 1 
	PerlSetVar XSLT template.xsl
	PerlSetVar XSLTCache 1
</Files>

<Files ~ (\.inc|\.htaccess)>
	ForceType text/plain
</Files>

# .ssi for full ssi support, with Apache::Filter
<Files ~ (\.ssi)>
	SetHandler perl-script
	PerlHandler Apache::ASP Apache::SSI
	PerlSetVar Global .
	PerlSetVar Filter On
</Files>

<Files ~ (\filter.filter)>
       SetHandler perl-script
       PerlHandler Apache::ASP Apache::ASP
       PerlSetVar Global .
       PerlSetVar Filter On
</Files>

<Files ~ (xml_subs_strict\.asp)>
	SetHandler perl-script
	PerlHandler Apache::ASP
	PerlSetVar CookiePath  /	
	PerlSetVar SessionTimeout  5
	PerlSetVar RegisterIncludes 1
	PerlSetVar XMLSubsMatch my:\w+
	PerlSetVar XMLSubsStrict 1
</Files>

# .html files for the ASP parsing, but not the $Session object
# NoState turns off $Session & $Application
<Files ~ (\.html)>
        SetHandler perl-script
        PerlHandler Apache::ASP
        PerlSetVar NoState 0
        PerlSetVar BufferingOn 1
        PerlSetVar NoCache 0
        PerlSetVar DebugBufferLength 500
</Files>
```


And I get this when I try to view the page:

```
Errors Output

   1. error compiling calendar.asp: maybe use strict error: Bareword found where operator expected at /home/kenneth/www/calendar.asp line 4, near "If Request" , /usr/local/share/perl/5.10.0/Apache/ASP.pm line 1466 

Debug Output

   1. RUN ASP (v2.61) for /home/kenneth/www/calendar.asp
   2. GlobalASA package Apache::ASP
   3. creating dbm for file /tmp/asp/server/internal, db SDBM_File, serializer: Data::Dumper
   4. creating dbm for file /tmp/asp/server/application, db SDBM_File, serializer: Data::Dumper
   5. session id from cookie: 0663a5407f7c802ee16b2fcd77757a27
   6. refreshing 0663a5407f7c802ee16b2fcd77757a27 with timeout 1226513772
   7. creating dbm for file /tmp/asp/06/0663a5407f7c802ee16b2fcd77757a27, db SDBM_File, serializer: Data::Dumper
   8. session not expired - time: 1226513472; timeout: 1226513765;
   9. tieing session 0663a5407f7c802ee16b2fcd77757a27
  10. parse file /home/kenneth/www/calendar.asp
  11. parsing /home/kenneth/www/calendar.asp
  12. start parse of data - 3846
  13. undefing sub Apache::ASP::__ASP__home_kenneth_www_calendar_aspx399322a5d013d9a909ebc17350480fc5xINC code CODE(0xb92e0f40)
  14. compiling into package Apache::ASP subid [Apache::ASP::__ASP__home_kenneth_www_calendar_aspx399322a5d013d9a909ebc17350480fc5xINC]
  15. undefing sub Apache::ASP::__ASP__home_kenneth_www_calendar_aspx399322a5d013d9a909ebc17350480fc5xINC code CODE(0xb92e0f40)
  16. error compiling calendar.asp: maybe use strict error: Bareword found where operator expected at /home/kenneth/www/calendar.asp line 4, near "If Request" , /usr/local/share/perl/5.10.0/Apache/ASP.pm line 1466
  17. ASP Done Processing Apache::ASP=HASH(0xb9994a58) - Application: Apache::ASP::Application=HASH(0xb95c4038); GlobalASA: Apache::ASP::GlobalASA=HASH(0xb92e1a40); Internal: Apache::ASP::State=HASH(0xb998ced8); Request: Apache::ASP::Request=HASH(0xb998f700); Response: Apache::ASP::Response=HASH(0xb92ed3c0); Server: Apache::ASP::Server=HASH(0xb95df9a0); Session: Apache::ASP::Session=HASH(0xb99948b8); app_state: 1; basename: calendar.asp; cleanup: ARRAY(0xb99946d8); compile_checksum: 399322a5d013d9a909ebc17350480fc5; compile_error: 1; compile_eval: SCALAR(0xb9994a48); compile_includes: 1; compile_perl_count: 1; cookie_domain: ; cookie_path: /; dbg: 4; debugs_output: ARRAY(0xb9994b38); destroy: 1; dir_config: APR::Table=HASH(0xb96df8e8); dirname: /home/kenneth/www/; errors_output: ARRAY(0xb99595f0); errs: 1; filename: /home/kenneth/www/calendar.asp; global: /home/kenneth/www//.; global_package: Apache::ASP; group_refresh: 30; headers_in: APR::Table=HASH(0xb99949a8); includes_dir: ARRAY(0xb998cd68); init_packages: ARRAY(0xb998f4e0); inode_names: ; lang_comment: #; lang_language: PerlScript; lang_module: Apache::ASP::Lang::PerlScript; lang_object: Apache::ASP::Lang::PerlScript=HASH(0xb998f790); last_time: 1226513472.5566; no_cache: ; package: Apache::ASP; paranoid_session: ; parse_config: 1; parse_file_count: 1; pod_comments: 1; r: Apache2::RequestRec=SCALAR(0xb92ed2e0); remote_ip: 9.161.61.39; request_binary_read: 1; search_dirs_cache: HASH(0xb95d0e60); secure_session: ; session_cookie: 1; session_count: 1; session_id: 0663a5407f7c802ee16b2fcd77757a27; session_serialize: ; session_state: 1; session_timeout: 300; session_url: 1; session_url_force: ; session_url_match: ; session_url_parse: 0; session_url_parse_match: ; start_time: 1226513472.54544; stat_inc: 0; stat_inc_match: 0; stat_scripts: 1; state_db: ; state_dir: /tmp/asp; state_manager: 10; state_serialize: ; state_serializer: ; ua: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-GB; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3; use_strict: 1; win32: 0; xml_subs_match: my:\w+; xml_subs_perl_args: 1; xml_subs_strict: ; xslt: ;
  18. errors out
  19. error compiling calendar.asp: maybe use strict error: Bareword found where operator expected at /home/kenneth/www/calendar.asp line 4, near "If Request" , /usr/local/share/perl/5.10.0/Apache/ASP.pm line 1466 

Compiled Data with Error 

  -: package Apache::ASP; ;; sub Apache::ASP::__ASP__home_kenneth_www_calendar_aspx399322a5d013d9a909ebc17350480fc5xINC {  ;; package Apache::ASP; ;; use strict;;;use vars qw($Application $Session $Response $Server $Request);;
  -: #line 1 /home/kenneth/www/calendar.asp
  1: ;;
  2: dim thisDate
  3: 
  4: If Request.Querystring("EventDate") = "" then
  5: 	thisDate = FormatDateTime(now(),2)
  6: else
  7: 	thisDate = Request.Querystring("EventDate")
  8: end if
  9: 	
 10: CurrentMonth = Month(thisDate)
 11: CurrentMonthName = MonthName(CurrentMonth)
 12: CurrentYear = Year(thisDate)
 13: 
 14: FirstDayDate = DateSerial(CurrentYear, CurrentMonth, 1)
 15: FirstDay = WeekDay(FirstDayDate, 0)
 16: CurrentDay = FirstDayDate
 17: testCurrentDay = date
 18: CurrentWeek = DatePart("ww",Request.querystring("EventDate"))
 19: 
 20: usDateFormat = ""& CurrentYear &"-"& CurrentMonth &"-"& Day(thisDate) &""
 21: 
 22: if not Request.Querystring("week") = "" then
 23: 	firstDayWeek = (dateadd( "d",(2-datepart("w",thisDate)),thisDate)-7)
 24: 	lastDayWeek = firstDayWeek + 6
 25: 
 26: 	if Day(lastDayWeek) <  Day(firstDayWeek) then
 27: 		myMonth = CurrentMonth - 1
 28: 		myYear = CurrentYear
 29: 		if myMonth = 0 then
 30: 			myMonth = 12
 31: 			myYear = CurrentYear - 1
 32: 		end if
 33: 	else
 34: 		myMonth = CurrentMonth
 35: 		myYear = CurrentYear
 36: 	end if
 37: 
 38: 	firsUsDateFormat = ""& myYear &"-"& myMonth &"-"& Day(firstDayWeek) &""
 39: 	endUsDateFormat = ""& CurrentYear &"-"& CurrentMonth &"-"& Day(lastDayWeek) &""
 40: end if
 41: 
 42: if not Request.Querystring("month") = "" then
 43: 
 44: end if
 45: ; &Apache::ASP::WriteRef($main::Response, \('
 46: 	<table cols="7" border="0" cellpadding="0" cellspacing="1">
 47: 
 48: 	<tr>
 49: 		<td align="center" bgcolor="Teal" style="background: #3f7dcd;">
 50: 			<A Href="default.asp?EventDate='.( Server.URLEncode(DateAdd("m",-1, thisDate))).(linkString).'"><</A>
 51: 		</td>
 52: 		<td colspan="5" align="center" bgcolor="Teal" style="background: #3f7dcd; color: white;">
 53: 			<b>'.( CurrentYear ).' - '.( CurrentMonthName ).'</b>
 54: 		</td>
 55: 		<td align="center" bgcolor="Teal" style="background: #3f7dcd;">
 56: 			<A Href="default.asp?EventDate='.( Server.URLEncode(DateAdd("m",1,thisDate))).(linkString).'">></A>
 57: 		</td>
 58: 	</tr>
 59: 	<tr>
 60: 		')); For DayLoop = 1 to 5; &Apache::ASP::WriteRef($main::Response, \('
 61: 			<td style="background: yellow; width: 30px;" align="center">'.( WeekDayName(Dayloop, True, 0)).'</td>
 62: 		')); Next; &Apache::ASP::WriteRef($main::Response, \('
 63: 		<td style="width: 30px; border: 0px;" align="center">&nbsp;</td>
 64: 		<td style="background: yellow; width: 30px;" align="center">W</td>
 65: 	</tr>
 66: 	<tr>'));
 67: 		If FirstDay <> 1 Then
 68: 			if FirstDay = 7 then; &Apache::ASP::WriteRef($main::Response, \('
 69: 				<td Colspan="6" style="border: 0px solid Black; background: #999999;">&nbsp;</td>'));
 70: 			else; &Apache::ASP::WriteRef($main::Response, \('
 71: 				<td Colspan="'.(FirstDay -1).'" style="border: 0px solid Black; background: #999999;">&nbsp;</td>'));
 72: 			End if
 73: 		End if
 74: 		DayCounter = FirstDay
 75: 		CorrectMonth = True
 76: 		dim holderName, todayDate
 77: 
 78: 		holderName = ""
 79: 		todayDate = "" 
 80: 
 81: 		Do While CorrectMonth = True
 82: 
 83: 			todayDate = ""& Day(CurrentDay) &"/"& CurrentMonth &"/"& CurrentYear &""			
 84: 			holderName = WeekdayName(Weekday(todayDate))
 85: 
 86: 			'If CurrentDay = EventDate Then
 87: 			If testCurrentDay = CurrentDay AND NOT holderName = "Sunday" AND NOT holderName = "Saturday" then; &Apache::ASP::WriteRef($main::Response, \('
 88: 				<td align="Center" style="background: red;"><A Href="default.asp?EventDate='.( Server.URLEncode(CurrentDay)).(linkString).'">'.(Day(CurrentDay)).'</A></td>'));
 89: 			ElseIf holderName = "Saturday" then; &Apache::ASP::WriteRef($main::Response, \('
 90: 				<td align="Center" style="border: 0px;">&nbsp;</td>'));
 91: 			ElseIf holderName = "Sunday" then; &Apache::ASP::WriteRef($main::Response, \('
 92: 				<td align="Center" style="background: #eaeaea;">
 93: 						<A Href="default.asp?EventDate='.( Server.URLEncode(CurrentDay)).(linkString).'&week='.(DatePart("ww",todayDate)-1).'">'.(DatePart("ww",todayDate)-1).'</A>
 94: 				</td>'));
 95: 			Else; &Apache::ASP::WriteRef($main::Response, \('
 96: 				<td align="Center" style="background: #eaeaea;"><A Href="default.asp?EventDate='.( Server.URLEncode(CurrentDay)).(linkString).'">'.(Day(CurrentDay)).'</A></td>
 97: 			')); End if; &Apache::ASP::WriteRef($main::Response, \('			
 98: 
 99: 			'));DayCounter = DayCounter + 1
100: 			If DayCounter > 7 then
101: 				DayCounter = 1; &Apache::ASP::WriteRef($main::Response, \('
102: 				</tr>
103: 				<tr>
104: 			'));End if
105: 
106: 			CurrentDay = DateAdd("d", 1, CurrentDay)
107: 
108: 			If Month(CurrentDay) <> CurrentMonth then
109: 				CorrectMonth = False
110: 			End if
111: 			holder = ""
112: 		Loop
113: 
114: 		IF DayCounter <> 1 Then; &Apache::ASP::WriteRef($main::Response, \('
115: 			<td Colspan="'.(8-DayCounter).'" style="border: 0px solid Black; background: #999999;"> </td>
116: 		')); End if; &Apache::ASP::WriteRef($main::Response, \('
117: 	</tr>
118: 	</table>')); ;; }


An error has occured with the Apache::ASP script just run. If you are the developer working on this script, and cannot work through this problem, please try researching it at the Apache::ASP web site, specifically the FAQ section. Failing that, check out your support options, and if necessary include this debug output with any query.
```

This is the first time I'm trying this out. Does anyone have any idea in which direction I should start troubleshooting? Or is it simply that the current "ASP" implementation I'm using isn't fully.. working/supported/ported?

A basic hello world doesn't work either:

*helloworld.html*

```
<html>
<body>
<%
response.write("Hello World!")
%>
</body>
</html>
```

```
error compiling helloworld.html: Bareword "response" not allowed while "strict subs" in use at /home/kenneth/www/helloworld.html line 4. , /usr/local/share/perl/5.10.0/Apache/ASP.pm line 1466
```

---

### Post by directhex on 2008-11-12
ASP and ASP.NET have nothing in common other than the name. mod_mono will not help you serve old ASP 3.0 pages

Apache::ASP perl module ONLY allows writing "ASP" pages in perl - i.e. your VBScript is no longer usable

Purchase [http://www.sun.com/software/chilisoft/](http://www.sun.com/software/chilisoft/) if you want classic ASP

---

### Post by fackamato on 2008-11-12
Ouch. Thanks for the reply though.

---

