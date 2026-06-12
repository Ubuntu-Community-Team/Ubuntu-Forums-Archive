---
title: "Mod-Perl 2 issues with Apache 2"
date: 2006-02-28
forum: Server Platforms
---

### Post by MrVain on 2006-02-28
Hi,
This is actually my 1st forum post ever, so please be gentle. This is also my first attempt at setting up a linux server (I used to be a windows guy... I like Ubuntu a lot though, first distribution of linux that is so friendly with me)
 
So I am setting up a web-server with Apache 2, PHP, MySQL and Perl/Mod-Perl. I installed all the proper packages. PHP & MySQL functionnal 100% - tested through PHPMyAdmin. PS I didnt use the server installtion mode, I wanted the GUI as I am not yet enough of an expert to use linux without it.
 
Perl / ModPerl is functionnal, but I have an issue with POST info. When I submit an HTML form printed out by a .pl file, the information wil submit OK for the first 4 times, and then on the 5th attempt, I get an error that tell me it cant create (in the MySQL DB) an item that I submitted on one of the 4 first attempts (yes I used different item names on all 5 attempts).
 
I tried a few things.
I read about persistent variables. I had a global variable in my script that I now declare as
>use vars qw($zo);
>$zo = undef;
>$zo = Zone->new("godmode");
instead of
>my $zo = Zone->new("godmode");
Zone being a personnal library. The reason Y I did this was because there were warning in apache 2 errors.log about variable 
 
In apache2.conf I added the following lines to handlw all .pl files anywhere. (I know it's not 100% safe, but this is a development server)
 
<Files ~ "\.pl$">
SetHandler perl-script
PerlResponseHandler ModPerl::Registry
PerlOptions +ParseHeaders
Options +ExecCGI
Order allow,deny
Allow from all
</Files>
 
 
Now I tried to slip somethingin there, I read elsewhere that said dto add
PerlInitHandler Apache::Reload
Supposed to reload all librairies automatically.
 
I constantly modify my library called Zone that creates 2 variables used within it (one of them being a CGI object) and that I read mod-Perl would not automatically reload the librairies.
>our ($db, $cgi);
>$cgi = undef;
>$db = undef;
>$cgi = new CGI;
 
Anyways, so now when I run my script I do not get anymore warnings in apache2 errors.log file. I couldnt use Apache::Reload as it does not appear to be installed, and I cant find it in Apt-get anywhere (neither through CPAN).
 
So I could provide you the whole apache2.conf file, or my whole script. But I didn't want to make this first post too big...
 
Any help would really be appreciated. Even if it is just providing me with the lines to handle .pl files with Perl interpreter (wihtout Mod-Perl).
 
TIA,
Fred

---

### Post by MrVain on 2006-02-28
Ok, so now I found out that I should use Apache2::Reload, thus my apache2.conf perl files section looks that way:
 
PerlModule Apache2::Reload
<Files ~ "\.pl$">
SetHandler perl-script
PerlInitHandler Apache2::Reload
PerlResponseHandler ModPerl::Registry
PerlOptions +ParseHeaders
Options +ExecCGI
Order allow,deny
Allow from all
</Files>

Unfortunately, after restarting apache2, the test still fails at 5th attempt.

---

