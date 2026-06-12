---
title: "Oracle Instant Client 21.6 causes coredump on Ubuntu 22.04 in PHP8.1 w/ oci8 module"
date: 2022-06-08
forum: Server Platforms
---

### Post by juu062 on 2022-06-08
[COLOR=#1A1A1B][FONT=&amp]Hello everybody,

[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp]I've been having an issue since I installed php-curl on my Ubuntu server over the weekend.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I've had a server running Ubuntu 20.04 LTS that ran PHP 7.4 w/ modules for imap, curl, mysql, pdo, pdo_mysql, pdo_oci, and oci8. This also included Oracle Instant Client 19.6 to connect to a database running (copied and pasted from querying v$version) Oracle Database 12c Enterprise Edition Release 12.2.0.1.0 - 64bit Production on a remote server.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]About a month ago, I upgraded to 22.04 with PHP 8.1. I did not immediately install imap or curl because I didn't need them at the time as they were only still installed on that server from a feature I'd removed from my site several years ago. Also, in addition to upgrading the OS, I also installed Instant Client 21.6. All was working fine.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Over the weekend, I was introducing a new feature on the site hosted on the server to grab email from an account and process actions on the replies through APIs, so I installed php-imap and php-curl. Immediately, any time I ran a script, the script would do everything as it was supposed to, including parts that used oci8/pdo_oci, imap, and curl. However, it would produce a coredump at the end.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]At first, any PHP script ran from the cli resulted in a coredump. Even something as simple as echo 2 * 2; and nothing else. I've checked the Apache error logs, and everything running through Apache appears to be fine.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I uninstalled php-imap and rebooted and still got messages that it was aborted with the coredumps. I reinstalled php-imap and uninstalled php-curl and the coredumps went away.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]However, reading the coredumps, it's actually an issue with the oracle instant client. Here is a link to the output of coredumpctl dump -- libclntsh.so.21.1 being one of libraries of the instant client.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][https://pastebin.com/M86NcEt0](https://pastebin.com/M86NcEt0)
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]So it would appear that something with php-curl is possibly interfering with the instant client?
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]So I began tinkering a way at this. A couple things I found:[/FONT][/COLOR]

[LIST]
[*]If pdo_oci is enabled on the server, a cli script will ALWAYS get a coredump upon execution, regardless of whether it uses pdo_oci or not.
[*]If I disable pdo_oci and instead use only oci8, I only get a coredump if I call oci_connect to make a connection. I tried what would happen if I made the connection but didn't query anything, and I do still get a coredump. I also tried putting in intentionally wrong arguments in oci_connect to see if it would coredump even if a connection was never made. It still coredumped.
[*][FONT=inherit]Since I still had the libraries for Instant Client 19.6 installed on the server, I tried using those instead, since they would still be compatible with the version of Oracle I'm using. I still get an identical coredump, with the only exception being the trace stack says the issues are encountered in libclntsh.so.19.1 instead of libclntsh.so.21.1, and the line numbers changed.[/FONT]
[/LIST]
[COLOR=#1A1A1B][FONT=&amp]

So the overall gist here is that something in php-curl seems to be conflicting with the Instant Client/oci8.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
As for installation sources:[/FONT][/COLOR]

[LIST]
[*]The Instant Client files were downloaded from Oracle, as I believe is the only way to install it, added with ldconfig, etc.
oci8 was installed from pecl, and added to php.ini
[*]pdo_oci, when it was enabled, was configure/make/make test from the ext/pdo_oci directory of the PHP source for that version of PHP, moved into the library directory, and added to php.ini.
[*][FONT=inherit]All other packages were installed directly from their appropriate php-[name] package from apt.[/FONT]
[/LIST]
[COLOR=#1A1A1B][FONT=&amp]
While I'd prefer to use pdo_oci, I'm fine just using the oci8 library if a fix is found for that, although I'm guessing a fix to whatever is causing the coredumps for oci8 will fix both since the errors are identical.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
Any help would be greatly appreciated!

Thank you![/FONT][/COLOR]

---

