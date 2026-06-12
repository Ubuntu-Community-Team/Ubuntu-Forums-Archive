---
title: "IRC server questions (looking for easy install/set-up)"
date: 2010-01-04
forum: Server Platforms
---

### Post by Th3Professor on 2010-01-04
I'd like to install an IRC server on my website (it's hosted on another server location). I can log into the server side of things but am not sure how much control I have of installing applications. I'd like an IRC that's easy to install and easy to set-up.

I logged into the cPanel page of the site and found this "general server information":

Operating system: Linux
Kernel version: 2.6.9-78.0.22.EL
Machine type: i686
Apache version: 1.3.41 (Unix)
PERL version: 5.8.8
PHP version: 4.4.7
MySQL version: 5.0.85-community
cPanel build: 11.24.5-STABLE 38506

Unfortunately there's not an IRCd/server type of application available on the "Fantistico Deluxe" application installer feature.

Any help would be greatly appreciated.

---

### Post by munky99999 on 2010-01-04
Assuming you can ssh into the box. Or get a console of some sort. For root access.

[https://help.ubuntu.com/community/IrcServer](https://help.ubuntu.com/community/IrcServer)

---

### Post by Th3Professor on 2010-01-04
> **munky99999 said:**
> Assuming you can ssh into the box. Or get a console of some sort. For root access.

[https://help.ubuntu.com/community/IrcServer](https://help.ubuntu.com/community/IrcServer)

I can ssh into it. I do not have "root" access. Only the access to the main account for the given domain. (Not "root" literally.)

---

### Post by Th3Professor on 2010-01-04
I've installed the hybrid irc daemon. Is there an easy/simple how-to on the config?

"**Note**: Remember to edit the ircd.conf file to personalize your servers settings."

edit-
as an addendum, or more like precursor, to the config file question...
When attempting to install the hybrid irc, it cut off short in the middle of the "make && make install" with an error not allowing it to go on due no permissions to mkdir in /usr/local. :( (sudo doesn't work, not in sudoers file)

---

### Post by Th3Professor on 2010-01-06
Are there any IRC server apps that will make it through an install without stopping/errors due to not having sudo permissions?

---

### Post by Project PWNED on 2010-01-06
Paste the output of the log. I'm assuming there is no access to gcc to compile the ircd. Is this a cPanel webhosting account? If so, you might not be allowed to run an ircd. An ircd shell will run you about $7/mo, usually includes DDoS protection for free which is a great thing to have. Or you could find a really cheap VPS for about $5/mo with about 128mb of RAM to run an ircd on, so you can have root access.

---

### Post by Th3Professor on 2010-01-06
> **Project PWNED said:**
> Paste the output of the log. I'm assuming there is no access to gcc to compile the ircd. Is this a cPanel webhosting account? If so, you might not be allowed to run an ircd. An ircd shell will run you about $7/mo, usually includes DDoS protection for free which is a great thing to have. Or you could find a really cheap VPS for about $5/mo with about 128mb of RAM to run an ircd on, so you can have root access.

Hmm. The pay per month thing is not an option.

It is a cPanel webhosting account.

Are there any IRC server apps that don't require root, that run in their specific location/directory?

---

### Post by Th3Professor on 2010-01-06
I found this:
"Ircd will work just  fine without root privileges."
Here:
[http://irchelp.org/irchelp/ircd/h7setup.html](http://irchelp.org/irchelp/ircd/h7setup.html)
...and that's Hybrid also.
I haven't tried following the "howto" steps on that page yet but will give it a try.
It seems like it'd be possible to run an IRC server *without* having to have root or sudo access.:confused:

edit-
I see this:
> To configure: 	cd to /<path to source>
        ./configure --prefix="/path/to/install/to"
(if you want to compile to the default directory, just do ./configure)
<hopefully that'll do the trick>

---

### Post by Project PWNED on 2010-01-07
Webhosting = not IRC hosting. This will not work, plain and simple, because you need gcc to compile Unreal. They will not allow you to run gcc (if they're smart) on a webhosting account, even with SSH access.

$5/mo will have to do or you will be without an irc server.

---

### Post by Th3Professor on 2010-01-08
The only conflict I've had with getting an IRC working via webhosting is the shared IP that my domain has with other domains under the same webhosting account. Is it possible to direct the IP in the IRCd config to a directory within an IP so it doesn't assume it's the entire network (within that IP)?

---

### Post by Project PWNED on 2010-01-08
So this shell account is letting you run gcc?

---

### Post by Th3Professor on 2010-01-09
I believe so, yes.

---

### Post by Project PWNED on 2010-01-09
You believe so? Type in gcc -v in your shell

---

### Post by Th3Professor on 2010-01-09
Here's gcc -v
> Reading specs from /usr/lib/gcc/i386-redhat-linux/3.4.6/specs
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --enable-shared --enable-threads=posix --disable-checking --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-java-awt=gtk --host=i386-redhat-linux
Thread model: posix
gcc version 3.4.6 20060404 (Red Hat 3.4.6-11)


---

### Post by Project PWNED on 2010-01-10
Well that eliminates one problem, my other would be if ircd tried to copy itself to /usr/bin or /usr/sbin, then attempted to bind to an IP address and port.

---

### Post by Th3Professor on 2010-01-10
> **Project PWNED said:**
> Well that eliminates one problem, my other would be if ircd tried to copy itself to /usr/bin or /usr/sbin, then attempted to bind to an IP address and port.

I used --export in the compile and it did not have any conflicts installing. It didn't try to copy itself into /usr/bin or similar.

I think the main concern right now might be regarding binding to IP address and port. I'm hitting a brick wall with that, not sure how to go about it.

The site shares an IP address with other sites (other domain names). If the ircd can bind to an IP address and a specific *port* within that address, to avoid attempting to use the entire thing, that'd be good. I don't know how to specify that.

---

### Post by Project PWNED on 2010-01-10
In the ircd configuration file, there will be a bind IP address and port section.

---

### Post by Th3Professor on 2010-01-10
My account on the server has /home/username.
It then has /public_html.
I've been trying to set IRC up in public_html, only because I know it's definitely a public access area for the account.
Should I install it in /home/username? Or in /home/username/(somewhere-else)/?

I tried installing it in /home/username/public_html/irc/ before, hence the:
irc.mysite.com/irc

For now, I'll ignore the "/irc" in the config file below.

Referring to the ircd (hybrid7) config file-

```

serverinfo {
    name = "irc.mysite.com";[COLOR=Red]     <--- I'll use "irc.mysite.com" for now.[/COLOR]
    sid = "_CHANGE_ME_";[COLOR=Red]     <--- Do I have to change this?[/COLOR]
    description = "MySite.com IRC Server";
    network_name = "-";
    network_desc = "-";
    hub = no;
    #vhost = "192.169.0.1";
    #vhost6 = "3ffe:80e8:546::2";
    max_clients = 512;
    #rsa_private_key_file = "/usr/local/ircd/etc/rsa.key";
    #ssl_certificate_file = "/usr/local/ircd/etc/cert.pem";
};

admin {
    name = "Professor";
    description = "Main Server Administrator";
    email = "<prof@mysite.com>";
};

log {
    use_logging = yes;
    fname_userlog = "logs/userlog";
    fname_operlog = "logs/operlog";
    fname_killlog = "logs/kill";
    fname_klinelog = "logs/kline";
    fname_glinelog = "logs/gline";
    log_level = L_INFO;
};

class {
    name = "users";
    ping_time = 90 seconds;
    number_per_ip = 2;
    max_local = 2;
    max_global = 10;
    max_number = 100;
    cidr_bitlen_ipv4 = 24;
    cidr_bitlen_ipv6 = 120;
    number_per_cidr = 16;
    sendq = 100 kbytes;
};

class {
    name = "opers";
    ping_time = 90 seconds;
    number_per_ip = 10;
    max_number = 100;
    sendq = 100kbytes;
};

class {
    name = "server";
    ping_time = 90 seconds;
    ping_warning = 15 seconds;
    connectfreq = 5 minutes;
    max_number = 1;
    sendq = 2 megabytes;
};

listen {
    port = 6665 .. 6669;[COLOR=Red]     <--- Should I change this?[/COLOR]
    flags = hidden, ssl;
    host = "192.168.0.1";[COLOR=Red]     <--- Or this?[/COLOR]
    port = 6697;[COLOR=Red]     <--- (or any of these others[/COLOR]
    host = "1.2.3.4";[COLOR=Red]     <--- "      " [/COLOR]
    port = 7000, 7001;[COLOR=Red]     <--- "      "[/COLOR]
    host = "3ffe:1234:a:b:c::d";[COLOR=Red]     <--- "      "[/COLOR]
    port = 7002;[COLOR=Red]     <--- "      ")[/COLOR]
};

auth {[COLOR=Red]     <--- These auth sections can be left alone, right?[/COLOR]
    user = "*@172.16.0.0/12";
    user = "*test@123D:B567:*";
    password = "letmein";
    encrypted = yes;
    spoof = "I.still.hate.packets";
    class = "opers";
    flags = need_password, spoof_notice, exceed_limit, kline_exempt,
        gline_exempt, resv_exempt, no_tilde, can_flood, can_idle;
};

auth {
    redirserv = "this.is.not.a.real.server";
    redirport = 6667;
    user = "*.server";
    class = "users";
};

auth {
    user = "*@*";
    class = "users";
    flags = need_ident;
};

operator {
    name = "god";
    user = "*god@*";
    user = "*@127.0.0.1";[COLOR=Red]     <--- Is this okay as is?[/COLOR]
    password = "etcnjl8juSU1E";[COLOR=Red]     <--- I can change the password with "mkpasswd".[/COLOR]
    encrypted = yes;
#    rsa_public_key_file = "/usr/local/ircd/etc/oper.pub";
    class = "opers";
#    umodes = locops, servnotice, operwall, wallop;
    flags = global_kill, remote, kline, unkline, xline,
        die, rehash, nick_changes, admin, operwall;
};

connect {
    name = "irc.mysite.com";[COLOR=Red]     <--- Using the "mysite.com" sample for now.[/COLOR]
    host = "192.168.0.1";
    vhost = "192.168.0.2";
    send_password = "password";[COLOR=Red]     <--- Leave this alone?[/COLOR]
    accept_password = "anotherpassword";[COLOR=Red]     <--- And this?[/COLOR]
    encrypted = no;
    port = 6666;[COLOR=Red]     <--- And this?[/COLOR]
    hub_mask = "*";
#    leaf_mask = "*.uk";
#    fakename = "*.arpa";
    class = "server";
#    flags = autoconn, lazylink, compressed, cryptlink, burst_away, topicburst;
};

connect {[COLOR=Red]     <--- Confusing, I thought I'd only need to fill in 1 "connect" section?[/COLOR]
    name = "encrypted.auth.example";
    host = "some.host.somewhere";
    port = 6667;
    flags = cryptlink;
    rsa_public_key_file = "etc/remote.server.keyfile";
#    cipher_preference = "BF/168";
};

connect "ipv6.some.server" {[COLOR=Red]     <--- (and another?)[/COLOR]
    host = "3ffd:dead:beef::1";
    send_password = "password";
    accept_password = "password";
    port = 6666;
    aftype = ipv6;
    class = "server";
};

cluster {
    name = "*.arpa";
    type = kline, unkline, locops, xline, resv;
};

shared {
    name = "irc2.some.server";
    user = "oper@my.host.is.spoofed";
    type = kline, unkline, resv;
};

kill {
    user = "bad@*.hacked.edu";
    reason = "Obviously hacked account";
};

kill {
    user = "^O[[:alpha:]]?[[:digit:]]+(x\.o|\.xo)$@^[[:alnum:]]{4}\.evilnet.org$";
    type = regex;
};

deny {
    ip = "10.0.1.0/24";
    reason = "Reconnecting vhosted bots";
};

exempt {
    ip = "192.168.0.0/16";
};

resv {
    reason = "There are no services on this network";
    nick = "nickserv";
    nick = "chanserv";
    channel = "#services";
    reason = "Clone bots";
    nick = "clone*";
};

gecos {
    name = "*sex*";
    reason = "Possible spambot";
};

gecos {
    name = "sub7server";
    reason = "Trojan drone";
};

gecos {
    name = "*http*";
    reason = "Spambot";
};

gecos {
    name = "^\[J[0o]hn Do[3e]\]-[0-9]{2,5}$";
    type = regex;
};

channel {
    disable_fake_channels = yes;
    restrict_channels = no;
    disable_local_channels = no;
    use_invex = yes;
    use_except = yes;
    use_knock = yes;
    knock_delay = 1 minutes;
    knock_delay_channel = 1 minute;
    burst_topicwho = yes;
    max_chans_per_user = 25;
    quiet_on_ban = yes;
    max_bans = 25;
    join_flood_count = 16;
    join_flood_time = 8 seconds;
    default_split_user_count = 0;
    default_split_server_count = 0;
    no_create_on_split = yes;
    no_join_on_split = no;
};

serverhide {
    flatten_links = no;
    links_delay = 5 minutes;
    hidden = no;
    disable_hidden = no;
    hide_servers = no;
    hidden_name = "*.hidden.com";
    hide_server_ips = no;
};

general {
    gline_min_cidr = 16;
    gline_min_cidr6 = 48;
    invisible_on_connect = yes;
    burst_away = no;
    use_whois_actually = yes;
    kill_chase_time_limit = 90;
    hide_spoof_ips = yes;
    ignore_bogus_ts = no;
    disable_auth = no;
    disable_remote_commands = no;
    tkline_expire_notices = no;
    default_floodcount = 10;
    failed_oper_notice = yes;
    dots_in_ident = 2;
    dot_in_ip6_addr = no;
    min_nonwildcard = 4;
    min_nonwildcard_simple = 3;
    max_accept = 20;
    anti_nick_flood = yes;
    max_nick_time = 20 seconds;
    max_nick_changes = 5;
    anti_spam_exit_message_time = 5 minutes;
    ts_warn_delta = 30 seconds;
    ts_max_delta = 5 minutes;
    kline_with_reason = yes;
    kline_reason = "Connection closed";
    reject_hold_time = 0;
    warn_no_nline = yes;
    stats_e_disabled = no;
    stats_o_oper_only = yes;
    stats_P_oper_only = yes;
    stats_i_oper_only = yes;
    stats_k_oper_only = yes;
    caller_id_wait = 1 minute;
    opers_bypass_callerid = no;
    pace_wait_simple = 1 second;
    pace_wait = 10 seconds;
    short_motd = no;
    ping_cookie = no;
    no_oper_flood = yes;
    true_no_oper_flood = yes;
    oper_pass_resv = yes;
    idletime = 0;
    max_targets = 4;
    client_flood = 2560 bytes;
    message_locale = "standard";
    oper_only_umodes = bots, cconn, cconn_full, debug, full, skill,
                           nchange, rej, spy, external, operwall,
                           locops, unauth;
    oper_umodes = bots, locops, servnotice, operwall, wallop;
    #servlink_path = "/usr/local/ircd/bin/servlink";
    #default_cipher_preference = "BF/168";
#    use_egd = yes;
#    egdpool_path = "/var/run/egd-pool";
#    compression_level = 6;
    throttle_time = 10;
};

glines {
    enable = yes;
    duration = 1 day;
    logging = reject, block;
    user = "god@I.still.hate.packets";[COLOR=Red]     <--- Leave this alone?[/COLOR]
    name = "hades.arpa";
    action = reject, block;
    user = "god@*";
    name = "*";
    action = block;
};

modules {[COLOR=Red]     <--- The only section I see that doesn't have /usr commented out.[/COLOR]
    path = "/usr/local/ircd/modules";
    path = "/usr/local/ircd/modules/autoload";
    #module = "some_module.so";
};

```So, I removed the "REMOVE ME" line that makes sure people go through the entire config file. Beyond that my main questions are in the red font above. The rest of it I hope is okay as is.

---

### Post by guessswh0 on 2010-01-11
any smart hosting company is going to see that you are running this, versus just hosting a website.  While they might not make you pay, be prepared for a probably ultimatum of taking it down or finding a new hosting company.

---

### Post by Th3Professor on 2010-01-11
> **Th3Professor said:**
> My account on the server has /home/username.
It then has /public_html.
I've been trying to set IRC up in public_html, only because I know it's definitely a public access area for the account.
Should I install it in /home/username? Or in /home/username/(somewhere-else)/?

I tried installing it in /home/username/public_html/irc/ before, hence the:
irc.mysite.com/irc

For now, I'll ignore the "/irc" in the config file below.

Referring to the ircd (hybrid7) config file-

```

serverinfo {
    name = "irc.mysite.com";[COLOR=Red]     <--- I'll use "irc.mysite.com" for now.[/COLOR]
    sid = "_CHANGE_ME_";[COLOR=Red]     <--- Do I have to change this?[/COLOR]
    description = "MySite.com IRC Server";
    network_name = "-";
    network_desc = "-";
    hub = no;
    #vhost = "192.169.0.1";
    #vhost6 = "3ffe:80e8:546::2";
    max_clients = 512;
    #rsa_private_key_file = "/usr/local/ircd/etc/rsa.key";
    #ssl_certificate_file = "/usr/local/ircd/etc/cert.pem";
};

admin {
    name = "Professor";
    description = "Main Server Administrator";
    email = "<prof@mysite.com>";
};

log {
    use_logging = yes;
    fname_userlog = "logs/userlog";
    fname_operlog = "logs/operlog";
    fname_killlog = "logs/kill";
    fname_klinelog = "logs/kline";
    fname_glinelog = "logs/gline";
    log_level = L_INFO;
};

class {
    name = "users";
    ping_time = 90 seconds;
    number_per_ip = 2;
    max_local = 2;
    max_global = 10;
    max_number = 100;
    cidr_bitlen_ipv4 = 24;
    cidr_bitlen_ipv6 = 120;
    number_per_cidr = 16;
    sendq = 100 kbytes;
};

class {
    name = "opers";
    ping_time = 90 seconds;
    number_per_ip = 10;
    max_number = 100;
    sendq = 100kbytes;
};

class {
    name = "server";
    ping_time = 90 seconds;
    ping_warning = 15 seconds;
    connectfreq = 5 minutes;
    max_number = 1;
    sendq = 2 megabytes;
};

listen {
    port = 6665 .. 6669;[COLOR=Red]     <--- Should I change this?[/COLOR]
    flags = hidden, ssl;
    host = "192.168.0.1";[COLOR=Red]     <--- Or this?[/COLOR]
    port = 6697;[COLOR=Red]     <--- (or any of these others[/COLOR]
    host = "1.2.3.4";[COLOR=Red]     <--- "      " [/COLOR]
    port = 7000, 7001;[COLOR=Red]     <--- "      "[/COLOR]
    host = "3ffe:1234:a:b:c::d";[COLOR=Red]     <--- "      "[/COLOR]
    port = 7002;[COLOR=Red]     <--- "      ")[/COLOR]
};

auth {[COLOR=Red]     <--- These auth sections can be left alone, right?[/COLOR]
    user = "*@172.16.0.0/12";
    user = "*test@123D:B567:*";
    password = "letmein";
    encrypted = yes;
    spoof = "I.still.hate.packets";
    class = "opers";
    flags = need_password, spoof_notice, exceed_limit, kline_exempt,
        gline_exempt, resv_exempt, no_tilde, can_flood, can_idle;
};

auth {
    redirserv = "this.is.not.a.real.server";
    redirport = 6667;
    user = "*.server";
    class = "users";
};

auth {
    user = "*@*";
    class = "users";
    flags = need_ident;
};

operator {
    name = "god";
    user = "*god@*";
    user = "*@127.0.0.1";[COLOR=Red]     <--- Is this okay as is?[/COLOR]
    password = "etcnjl8juSU1E";[COLOR=Red]     <--- I can change the password with "mkpasswd".[/COLOR]
    encrypted = yes;
#    rsa_public_key_file = "/usr/local/ircd/etc/oper.pub";
    class = "opers";
#    umodes = locops, servnotice, operwall, wallop;
    flags = global_kill, remote, kline, unkline, xline,
        die, rehash, nick_changes, admin, operwall;
};

connect {
    name = "irc.mysite.com";[COLOR=Red]     <--- Using the "mysite.com" sample for now.[/COLOR]
    host = "192.168.0.1";
    vhost = "192.168.0.2";
    send_password = "password";[COLOR=Red]     <--- Leave this alone?[/COLOR]
    accept_password = "anotherpassword";[COLOR=Red]     <--- And this?[/COLOR]
    encrypted = no;
    port = 6666;[COLOR=Red]     <--- And this?[/COLOR]
    hub_mask = "*";
#    leaf_mask = "*.uk";
#    fakename = "*.arpa";
    class = "server";
#    flags = autoconn, lazylink, compressed, cryptlink, burst_away, topicburst;
};

connect {[COLOR=Red]     <--- Confusing, I thought I'd only need to fill in 1 "connect" section?[/COLOR]
    name = "encrypted.auth.example";
    host = "some.host.somewhere";
    port = 6667;
    flags = cryptlink;
    rsa_public_key_file = "etc/remote.server.keyfile";
#    cipher_preference = "BF/168";
};

connect "ipv6.some.server" {[COLOR=Red]     <--- (and another?)[/COLOR]
    host = "3ffd:dead:beef::1";
    send_password = "password";
    accept_password = "password";
    port = 6666;
    aftype = ipv6;
    class = "server";
};

cluster {
    name = "*.arpa";
    type = kline, unkline, locops, xline, resv;
};

shared {
    name = "irc2.some.server";
    user = "oper@my.host.is.spoofed";
    type = kline, unkline, resv;
};

kill {
    user = "bad@*.hacked.edu";
    reason = "Obviously hacked account";
};

kill {
    user = "^O[[:alpha:]]?[[:digit:]]+(x\.o|\.xo)$@^[[:alnum:]]{4}\.evilnet.org$";
    type = regex;
};

deny {
    ip = "10.0.1.0/24";
    reason = "Reconnecting vhosted bots";
};

exempt {
    ip = "192.168.0.0/16";
};

resv {
    reason = "There are no services on this network";
    nick = "nickserv";
    nick = "chanserv";
    channel = "#services";
    reason = "Clone bots";
    nick = "clone*";
};

gecos {
    name = "*sex*";
    reason = "Possible spambot";
};

gecos {
    name = "sub7server";
    reason = "Trojan drone";
};

gecos {
    name = "*http*";
    reason = "Spambot";
};

gecos {
    name = "^\[J[0o]hn Do[3e]\]-[0-9]{2,5}$";
    type = regex;
};

channel {
    disable_fake_channels = yes;
    restrict_channels = no;
    disable_local_channels = no;
    use_invex = yes;
    use_except = yes;
    use_knock = yes;
    knock_delay = 1 minutes;
    knock_delay_channel = 1 minute;
    burst_topicwho = yes;
    max_chans_per_user = 25;
    quiet_on_ban = yes;
    max_bans = 25;
    join_flood_count = 16;
    join_flood_time = 8 seconds;
    default_split_user_count = 0;
    default_split_server_count = 0;
    no_create_on_split = yes;
    no_join_on_split = no;
};

serverhide {
    flatten_links = no;
    links_delay = 5 minutes;
    hidden = no;
    disable_hidden = no;
    hide_servers = no;
    hidden_name = "*.hidden.com";
    hide_server_ips = no;
};

general {
    gline_min_cidr = 16;
    gline_min_cidr6 = 48;
    invisible_on_connect = yes;
    burst_away = no;
    use_whois_actually = yes;
    kill_chase_time_limit = 90;
    hide_spoof_ips = yes;
    ignore_bogus_ts = no;
    disable_auth = no;
    disable_remote_commands = no;
    tkline_expire_notices = no;
    default_floodcount = 10;
    failed_oper_notice = yes;
    dots_in_ident = 2;
    dot_in_ip6_addr = no;
    min_nonwildcard = 4;
    min_nonwildcard_simple = 3;
    max_accept = 20;
    anti_nick_flood = yes;
    max_nick_time = 20 seconds;
    max_nick_changes = 5;
    anti_spam_exit_message_time = 5 minutes;
    ts_warn_delta = 30 seconds;
    ts_max_delta = 5 minutes;
    kline_with_reason = yes;
    kline_reason = "Connection closed";
    reject_hold_time = 0;
    warn_no_nline = yes;
    stats_e_disabled = no;
    stats_o_oper_only = yes;
    stats_P_oper_only = yes;
    stats_i_oper_only = yes;
    stats_k_oper_only = yes;
    caller_id_wait = 1 minute;
    opers_bypass_callerid = no;
    pace_wait_simple = 1 second;
    pace_wait = 10 seconds;
    short_motd = no;
    ping_cookie = no;
    no_oper_flood = yes;
    true_no_oper_flood = yes;
    oper_pass_resv = yes;
    idletime = 0;
    max_targets = 4;
    client_flood = 2560 bytes;
    message_locale = "standard";
    oper_only_umodes = bots, cconn, cconn_full, debug, full, skill,
                           nchange, rej, spy, external, operwall,
                           locops, unauth;
    oper_umodes = bots, locops, servnotice, operwall, wallop;
    #servlink_path = "/usr/local/ircd/bin/servlink";
    #default_cipher_preference = "BF/168";
#    use_egd = yes;
#    egdpool_path = "/var/run/egd-pool";
#    compression_level = 6;
    throttle_time = 10;
};

glines {
    enable = yes;
    duration = 1 day;
    logging = reject, block;
    user = "god@I.still.hate.packets";[COLOR=Red]     <--- Leave this alone?[/COLOR]
    name = "hades.arpa";
    action = reject, block;
    user = "god@*";
    name = "*";
    action = block;
};

modules {[COLOR=Red]     <--- The only section I see that doesn't have /usr commented out.[/COLOR]
    path = "/usr/local/ircd/modules";
    path = "/usr/local/ircd/modules/autoload";
    #module = "some_module.so";
};

```So, I removed the "REMOVE ME" line that makes sure people go through the entire config file. Beyond that my main questions are in the red font above. The rest of it I hope is okay as is.

My questions still stand. Thank you to anybody for their input and help with this. :KS

---

### Post by Project PWNED on 2010-01-11
[QUOTE=Th3Professor;8644058]
```

serverinfo {
    name = "domain.com";[COLOR=Red]     <--- you can use a domain, IP address, or setup a irc.domain.com DNS[/COLOR]
    sid = "ircd";[COLOR=Red]     <--- changed[/COLOR]
    description = "MySite.com IRC Server";
    network_name = "-";
    network_desc = "-";
    hub = no;
    #vhost = "192.169.0.1";
    #vhost6 = "3ffe:80e8:546::2";
    max_clients = 512;
    #rsa_private_key_file = "/usr/local/ircd/etc/rsa.key";
    #ssl_certificate_file = "/usr/local/ircd/etc/cert.pem";
};

admin {
    name = "Professor";
    description = "Main Server Administrator";
    email = "<prof@mysite.com>";
};

log {
    use_logging = yes;
    fname_userlog = "logs/userlog";
    fname_operlog = "logs/operlog";
    fname_killlog = "logs/kill";
    fname_klinelog = "logs/kline";
    fname_glinelog = "logs/gline";
    log_level = L_INFO;
};

class {
    name = "users";
    ping_time = 90 seconds;
    number_per_ip = 2;
    max_local = 2;
    max_global = 10;
    max_number = 100;
    cidr_bitlen_ipv4 = 24;
    cidr_bitlen_ipv6 = 120;
    number_per_cidr = 16;
    sendq = 100 kbytes;
};

class {
    name = "opers";
    ping_time = 90 seconds;
    number_per_ip = 10;
    max_number = 100;
    sendq = 100kbytes;
};

class {
    name = "server";
    ping_time = 90 seconds;
    ping_warning = 15 seconds;
    connectfreq = 5 minutes;
    max_number = 1;
    sendq = 2 megabytes;
};

listen {
    port = 6665 .. 6669;[COLOR=Red]     <--- 6665-6669 is standard[/COLOR]
    flags = hidden, ssl;
    host = "bind.ip.address";[COLOR=Red]     <--- ip address you wanted to bind to[/COLOR]
    port = 6697;[COLOR=Red]     <--- ircd ssl port[/COLOR]
    host = "bind.ip.address";[COLOR=Red]     <--- "      " [/COLOR]
    port = 7000, 7001;[COLOR=Red]     <--- "sometimes used on another ip address on the machine      "[/COLOR]
    host = "3ffe:1234:a:b:c::d";[COLOR=Red]     <--- "ipv6      "[/COLOR]
    port = 7002;[COLOR=Red]     <--- "trying to bind ipv6 address to specific port      ")[/COLOR]
};

auth {[COLOR=Red]     <--- looks good for an oper block[/COLOR]
    user = "*@172.16.0.0/12";
    user = "*test@123D:B567:*";
    password = "letmein";
    encrypted = yes;
    spoof = "I.still.hate.packets";
    class = "opers";
    flags = need_password, spoof_notice, exceed_limit, kline_exempt,
        gline_exempt, resv_exempt, no_tilde, can_flood, can_idle;
};

auth {
    redirserv = "this.is.not.a.real.server";
    redirport = 6667;
    user = "*.server";
    class = "users";
};

auth {
    user = "*@*";
    class = "users";
    flags = need_ident;
};

operator {
    name = "god";
    user = "*god@*";
    user = "*@127.0.0.1";[COLOR=Red]     <--- only if you connect from 127.0.0.1 or localhost, on the box, and specific the hostname in your irc client[/COLOR]
    password = "etcnjl8juSU1E";[COLOR=Red]     <--- looks good.[/COLOR]
    encrypted = yes;
#    rsa_public_key_file = "/usr/local/ircd/etc/oper.pub";
    class = "opers";
#    umodes = locops, servnotice, operwall, wallop;
    flags = global_kill, remote, kline, unkline, xline,
        die, rehash, nick_changes, admin, operwall;
};

connect {
    name = "irc.mysite.com";[COLOR=Red]     <--- Using the "mysite.com" sample for now.[/COLOR]
    host = "192.168.0.1";
    vhost = "192.168.0.2";
    send_password = "password";[COLOR=Red]     <--- Leave this alone?[/COLOR]
    accept_password = "anotherpassword";[COLOR=Red]     <--- And this?[/COLOR]
    encrypted = no;
    port = 6666;[COLOR=Red]     <--- And this?[/COLOR]
    hub_mask = "*";
#    leaf_mask = "*.uk";
#    fakename = "*.arpa";
    class = "server";
#    flags = autoconn, lazylink, compressed, cryptlink, burst_away, topicburst;
};

connect {[COLOR=Red]     <--- Connecting remote server/leaf [/COLOR]
    name = "encrypted.auth.example";
    host = "some.host.somewhere";
    port = 6667;
    flags = cryptlink;
    rsa_public_key_file = "etc/remote.server.keyfile";
#    cipher_preference = "BF/168";
};

connect "ipv6.some.server" {[COLOR=Red]     <--- example to link in a remote ipv6 server[/COLOR]
    host = "3ffd:dead:beef::1";
    send_password = "password";
    accept_password = "password";
    port = 6666;
    aftype = ipv6;
    class = "server";
};

cluster {
    name = "*.arpa";
    type = kline, unkline, locops, xline, resv;
};

shared {
    name = "irc2.some.server";
    user = "oper@my.host.is.spoofed";
    type = kline, unkline, resv;
};

kill {
    user = "bad@*.hacked.edu";
    reason = "Obviously hacked account";
};

kill {
    user = "^O[[:alpha:]]?[[:digit:]]+(x\.o|\.xo)$@^[[:alnum:]]{4}\.evilnet.org$";
    type = regex;
};

deny {
    ip = "10.0.1.0/24";
    reason = "Reconnecting vhosted bots";
};

exempt {
    ip = "192.168.0.0/16";
};

resv {
    reason = "There are no services on this network";
    nick = "nickserv";
    nick = "chanserv";
    channel = "#services";
    reason = "Clone bots";
    nick = "clone*";
};

gecos {
    name = "*sex*";
    reason = "Possible spambot";
};

gecos {
    name = "sub7server";
    reason = "Trojan drone";
};

gecos {
    name = "*http*";
    reason = "Spambot";
};

gecos {
    name = "^\[J[0o]hn Do[3e]\]-[0-9]{2,5}$";
    type = regex;
};

channel {
    disable_fake_channels = yes;
    restrict_channels = no;
    disable_local_channels = no;
    use_invex = yes;
    use_except = yes;
    use_knock = yes;
    knock_delay = 1 minutes;
    knock_delay_channel = 1 minute;
    burst_topicwho = yes;
    max_chans_per_user = 25;
    quiet_on_ban = yes;
    max_bans = 25;
    join_flood_count = 16;
    join_flood_time = 8 seconds;
    default_split_user_count = 0;
    default_split_server_count = 0;
    no_create_on_split = yes;
    no_join_on_split = no;
};

serverhide {
    flatten_links = no;
    links_delay = 5 minutes;
    hidden = no;
    disable_hidden = no;
    hide_servers = no;
    hidden_name = "*.hidden.com";
    hide_server_ips = no;
};

general {
    gline_min_cidr = 16;
    gline_min_cidr6 = 48;
    invisible_on_connect = yes;
    burst_away = no;
    use_whois_actually = yes;
    kill_chase_time_limit = 90;
    hide_spoof_ips = yes;
    ignore_bogus_ts = no;
    disable_auth = no;
    disable_remote_commands = no;
    tkline_expire_notices = no;
    default_floodcount = 10;
    failed_oper_notice = yes;
    dots_in_ident = 2;
    dot_in_ip6_addr = no;
    min_nonwildcard = 4;
    min_nonwildcard_simple = 3;
    max_accept = 20;
    anti_nick_flood = yes;
    max_nick_time = 20 seconds;
    max_nick_changes = 5;
    anti_spam_exit_message_time = 5 minutes;
    ts_warn_delta = 30 seconds;
    ts_max_delta = 5 minutes;
    kline_with_reason = yes;
    kline_reason = "Connection closed";
    reject_hold_time = 0;
    warn_no_nline = yes;
    stats_e_disabled = no;
    stats_o_oper_only = yes;
    stats_P_oper_only = yes;
    stats_i_oper_only = yes;
    stats_k_oper_only = yes;
    caller_id_wait = 1 minute;
    opers_bypass_callerid = no;
    pace_wait_simple = 1 second;
    pace_wait = 10 seconds;
    short_motd = no;
    ping_cookie = no;
    no_oper_flood = yes;
    true_no_oper_flood = yes;
    oper_pass_resv = yes;
    idletime = 0;
    max_targets = 4;
    client_flood = 2560 bytes;
    message_locale = "standard";
    oper_only_umodes = bots, cconn, cconn_full, debug, full, skill,
                           nchange, rej, spy, external, operwall,
                           locops, unauth;
    oper_umodes = bots, locops, servnotice, operwall, wallop;
    #servlink_path = "/usr/local/ircd/bin/servlink";
    #default_cipher_preference = "BF/168";
#    use_egd = yes;
#    egdpool_path = "/var/run/egd-pool";
#    compression_level = 6;
    throttle_time = 10;
};

glines {
    enable = yes;
    duration = 1 day;
    logging = reject, block;
    user = "god@I.still.hate.packets";[COLOR=Red]     <--- this is a gline block, are you trying to gline that user/vhost?[/COLOR]
    name = "hades.arpa";
    action = reject, block;
    user = "god@*";
    name = "*";
    action = block;
};

modules {[COLOR=Red]     <--- Change this to /home/username/ircd/modules/.. etc.. etc..[/COLOR]
    path = "/usr/local/ircd/modules";
    path = "/usr/local/ircd/modules/autoload";
    #module = "some_module.so";
};

```

---

### Post by Project PWNED on 2010-01-11
Like mentioned, I think the firewall this box is behind is most likely going to block these IRCD ports (if they were smart), but - if they were smart they would limit gcc access to users. If they were smart, again, they would only allow 80/tcp and 445/tcp to connect to the machine.

Worst comes to worse, like mentioned, they will see you doing this and terminate your account. I doubt they're going to approach you into paying to host an ircd account because your provider would already offer ircd accounts in their hosting packages.

---

### Post by Th3Professor on 2010-01-11
I just confirmed with the host provider. It is not a limited 'webhosting' service. It is an entirely dedicated server that I *do have permission* to install IRC servers onto.

---

### Post by Th3Professor on 2010-01-11
That's weird. Your reply wasn't there when I sent my previous reply and yet it was posted 3 hours before mine. Spooky. I probably just missed it. Anyway...

> **Project PWNED said:**
> Like mentioned, I think the firewall this box is behind is most likely going to block these IRCD ports (if they were smart), but - if they were smart they would limit gcc access to users.
"They" = a person I personally know and they've told me that it is completely okay to run an IRCd. They didn't say there are blocked ports, nor limited gcc access. However, I'll ask them specifically about those 2 things just to get confirmation of permissions on the server.

> **Project PWNED said:**
> If they were smart, again, they would only allow 80/tcp and 445/tcp to connect to the machine.
I'll ask them about that too. The "box"/server that they are running... they are 100% in control of who can and cannot receive hosting from them. It's basically all in-house, aka family and friends. I doubt the access/permissions/etc. topic is really a concern but I'll ask about these specific things you mentioned anyway just to play it safe and make sure.

> **Project PWNED said:**
> Worst comes to worse, like mentioned, they will see you doing this and terminate your account. I doubt they're going to approach you into paying to host an ircd account because your provider would already offer ircd accounts in their hosting packages.
I am 100% confident that my account will not be terminated. They personally told me that I **can** run an IRC server through them.

Anyway, I just noticed your other reply included the code (ircd.conf) revised with your comments. Thank you for the feedback. I've updated it again in response to your comments (this time in blue font to keep things clear).

```

serverinfo {
    name = "domain.com";[COLOR=Red]     <--- you can use a domain, IP address, or setup a irc.domain.com DNS [COLOR=Blue]Can I use a subdirectory like "irc.mysite.com/irc"?[/COLOR][/COLOR]
    sid = "ircd";[COLOR=Red]     <--- changed[/COLOR] [COLOR=Blue]So the SID doesn't have to be letter-number-number (like "A35" or similar, as suggested in the original conf file)?[/COLOR]
    description = "MySite.com IRC Server";
    network_name = "-";
    network_desc = "-";
    hub = no;
    #vhost = "192.169.0.1";
    #vhost6 = "3ffe:80e8:546::2";
    max_clients = 512;
    #rsa_private_key_file = "/usr/local/ircd/etc/rsa.key";
    #ssl_certificate_file = "/usr/local/ircd/etc/cert.pem";
};

admin {
    name = "Professor";
    description = "Main Server Administrator";
    email = "<prof@mysite.com>";
};

log {
    use_logging = yes;
    fname_userlog = "logs/userlog";
    fname_operlog = "logs/operlog";
    fname_killlog = "logs/kill";
    fname_klinelog = "logs/kline";
    fname_glinelog = "logs/gline";
    log_level = L_INFO;
};

class {
    name = "users";
    ping_time = 90 seconds;
    number_per_ip = 2;
    max_local = 2;
    max_global = 10;
    max_number = 100;
    cidr_bitlen_ipv4 = 24;
    cidr_bitlen_ipv6 = 120;
    number_per_cidr = 16;
    sendq = 100 kbytes;
};

class {
    name = "opers";
    ping_time = 90 seconds;
    number_per_ip = 10;
    max_number = 100;
    sendq = 100kbytes;
};

class {
    name = "server";
    ping_time = 90 seconds;
    ping_warning = 15 seconds;
    connectfreq = 5 minutes;
    max_number = 1;
    sendq = 2 megabytes;
};

listen {
    port = 6665 .. 6669;[COLOR=Red]     <--- 6665-6669 is standard[/COLOR]
    flags = hidden, ssl;
    host = "bind.ip.address";[COLOR=Red]     <--- ip address you wanted to bind to[/COLOR] [COLOR=Blue]Would that be the IP address of the domain/server that the IRCd is installed on?[/COLOR]
    port = 6697;[COLOR=Red]     <--- ircd ssl port[/COLOR]
    host = "bind.ip.address";[COLOR=Red]     <--- "      " [/COLOR][COLOR=Blue]Should I change this to the same IP address 2 lines up?[/COLOR]
    port = 7000, 7001;[COLOR=Red]     <--- "sometimes used on another ip address on the machine      "[/COLOR]
    host = "3ffe:1234:a:b:c::d";[COLOR=Red]     <--- "ipv6      "[/COLOR] [COLOR=Blue]Will I need to retrieve the ipv6 version of my domain's/server's IP address (that the IRCd is installed on) and insert that in here?[/COLOR]
    port = 7002;[COLOR=Red]     <--- "trying to bind ipv6 address to specific port      ")[/COLOR]
};

auth {[COLOR=Red]     <--- looks good for an oper block[/COLOR]
    user = "*@172.16.0.0/12";
    user = "*test@123D:B567:*";
    password = "letmein";
    encrypted = yes;
    spoof = "I.still.hate.packets";
    class = "opers";
    flags = need_password, spoof_notice, exceed_limit, kline_exempt,
        gline_exempt, resv_exempt, no_tilde, can_flood, can_idle;
};

auth {
    redirserv = "this.is.not.a.real.server";
    redirport = 6667;
    user = "*.server";
    class = "users";
};

auth {
    user = "*@*";
    class = "users";
    flags = need_ident;
};

operator {
    name = "god";
    user = "*god@*";
    user = "*@127.0.0.1";[COLOR=Red]     <--- only if you connect from 127.0.0.1 or localhost, on the box, and specific the hostname in your irc client [COLOR=Blue]This part is confusing. :-\[/COLOR][/COLOR][COLOR=Blue] Should I just leave this part alone?[/COLOR]
    password = "etcnjl8juSU1E";[COLOR=Red]     <--- looks good.[/COLOR]
    encrypted = yes;
#    rsa_public_key_file = "/usr/local/ircd/etc/oper.pub";
    class = "opers";
#    umodes = locops, servnotice, operwall, wallop;
    flags = global_kill, remote, kline, unkline, xline,
        die, rehash, nick_changes, admin, operwall;
};

connect { [COLOR=Blue]<--- Would I need to change the passwords in this section or just leave this part alone?[/COLOR]
    name = "irc.mysite.com";[COLOR=Red]     <--- Using the "mysite.com" sample for now.[/COLOR]
    host = "192.168.0.1";
    vhost = "192.168.0.2";
    send_password = "password";[COLOR=Red]     <--- Leave this alone?[/COLOR]
    accept_password = "anotherpassword";[COLOR=Red]     <--- And this?[/COLOR]
    encrypted = no;
    port = 6666;[COLOR=Red]     <--- And this?[/COLOR]
    hub_mask = "*";
#    leaf_mask = "*.uk";
#    fakename = "*.arpa";
    class = "server";
#    flags = autoconn, lazylink, compressed, cryptlink, burst_away, topicburst;
};

connect {[COLOR=Red]     <--- Connecting remote server/leaf [COLOR=Blue](Another confusing section) :-\[/COLOR][/COLOR][COLOR=Blue] And not sure what "leaf" is.[/COLOR]
    name = "encrypted.auth.example";
    host = "some.host.somewhere";
    port = 6667;
    flags = cryptlink;
    rsa_public_key_file = "etc/remote.server.keyfile";
#    cipher_preference = "BF/168";
};

connect "ipv6.some.server" {[COLOR=Red]     <--- example to link in a remote ipv6 server[/COLOR] [COLOR=Blue]Leave this alone also? Or change the "password" stuff/etc.?[/COLOR]
    host = "3ffd:dead:beef::1";
    send_password = "password";
    accept_password = "password";
    port = 6666;
    aftype = ipv6;
    class = "server";
};

cluster {
    name = "*.arpa";
    type = kline, unkline, locops, xline, resv;
};

shared {
    name = "irc2.some.server";
    user = "oper@my.host.is.spoofed";
    type = kline, unkline, resv;
};

kill {
    user = "bad@*.hacked.edu";
    reason = "Obviously hacked account";
};

kill {
    user = "^O[[:alpha:]]?[[:digit:]]+(x\.o|\.xo)$@^[[:alnum:]]{4}\.evilnet.org$";
    type = regex;
};

deny {
    ip = "10.0.1.0/24";
    reason = "Reconnecting vhosted bots";
};

exempt {
    ip = "192.168.0.0/16";
};

resv {
    reason = "There are no services on this network";
    nick = "nickserv";
    nick = "chanserv";
    channel = "#services";
    reason = "Clone bots";
    nick = "clone*";
};

gecos {
    name = "*sex*";
    reason = "Possible spambot";
};

gecos {
    name = "sub7server";
    reason = "Trojan drone";
};

gecos {
    name = "*http*";
    reason = "Spambot";
};

gecos {
    name = "^\[J[0o]hn Do[3e]\]-[0-9]{2,5}$";
    type = regex;
};

channel {
    disable_fake_channels = yes;
    restrict_channels = no;
    disable_local_channels = no;
    use_invex = yes;
    use_except = yes;
    use_knock = yes;
    knock_delay = 1 minutes;
    knock_delay_channel = 1 minute;
    burst_topicwho = yes;
    max_chans_per_user = 25;
    quiet_on_ban = yes;
    max_bans = 25;
    join_flood_count = 16;
    join_flood_time = 8 seconds;
    default_split_user_count = 0;
    default_split_server_count = 0;
    no_create_on_split = yes;
    no_join_on_split = no;
};

serverhide {
    flatten_links = no;
    links_delay = 5 minutes;
    hidden = no;
    disable_hidden = no;
    hide_servers = no;
    hidden_name = "*.hidden.com";
    hide_server_ips = no;
};

general {
    gline_min_cidr = 16;
    gline_min_cidr6 = 48;
    invisible_on_connect = yes;
    burst_away = no;
    use_whois_actually = yes;
    kill_chase_time_limit = 90;
    hide_spoof_ips = yes;
    ignore_bogus_ts = no;
    disable_auth = no;
    disable_remote_commands = no;
    tkline_expire_notices = no;
    default_floodcount = 10;
    failed_oper_notice = yes;
    dots_in_ident = 2;
    dot_in_ip6_addr = no;
    min_nonwildcard = 4;
    min_nonwildcard_simple = 3;
    max_accept = 20;
    anti_nick_flood = yes;
    max_nick_time = 20 seconds;
    max_nick_changes = 5;
    anti_spam_exit_message_time = 5 minutes;
    ts_warn_delta = 30 seconds;
    ts_max_delta = 5 minutes;
    kline_with_reason = yes;
    kline_reason = "Connection closed";
    reject_hold_time = 0;
    warn_no_nline = yes;
    stats_e_disabled = no;
    stats_o_oper_only = yes;
    stats_P_oper_only = yes;
    stats_i_oper_only = yes;
    stats_k_oper_only = yes;
    caller_id_wait = 1 minute;
    opers_bypass_callerid = no;
    pace_wait_simple = 1 second;
    pace_wait = 10 seconds;
    short_motd = no;
    ping_cookie = no;
    no_oper_flood = yes;
    true_no_oper_flood = yes;
    oper_pass_resv = yes;
    idletime = 0;
    max_targets = 4;
    client_flood = 2560 bytes;
    message_locale = "standard";
    oper_only_umodes = bots, cconn, cconn_full, debug, full, skill,
                           nchange, rej, spy, external, operwall,
                           locops, unauth;
    oper_umodes = bots, locops, servnotice, operwall, wallop;
    #servlink_path = "/usr/local/ircd/bin/servlink";
    #default_cipher_preference = "BF/168";
#    use_egd = yes;
#    egdpool_path = "/var/run/egd-pool";
#    compression_level = 6;
    throttle_time = 10;
};

glines {
    enable = yes;
    duration = 1 day;
    logging = reject, block;
    user = "god@I.still.hate.packets";[COLOR=Red]     <--- this is a gline block, are you trying to gline that user/vhost?[/COLOR] [COLOR=Blue]This line was default to the original example ircd.conf file. I figured just leave it as is. (?)[/COLOR]
    name = "hades.arpa";
    action = reject, block;
    user = "god@*";
    name = "*";
    action = block;
};

modules {[COLOR=Red]     <--- Change this to /home/username/ircd/modules/.. etc.. etc..[/COLOR] [COLOR=Blue]Ah! Awesome, thank you! That makes perfect sense. :-)[/COLOR]
    path = "/usr/local/ircd/modules";
    path = "/usr/local/ircd/modules/autoload";
    #module = "some_module.so";
};

```

That last part (modules) brings up the question of install directory.
Should I install the IRCd in /home/username/ircd instead of /home/username/public_html/ircd? (or "irc" instead of "ircd") Or does it really matter?

Thanks. :)

---

### Post by Project PWNED on 2010-01-11
I would not install it in public_html, you'd have to put index.html's in each directory so nobody could access it via [http://domain/irc/modules](http://domain/irc/modules) etc etc

---

### Post by Th3Professor on 2010-01-12
Sounds good... /home/username/irc will be the install directory. Thank you for the feedback.

I've updated the config file with add-on questions (in blue), I'll remove the rest of the config file (except for the "name {" beginning of the sections with questions)...

> 
** serverinfo** {
    name = "domain.com";[COLOR=Red]     <--- you can use a domain, IP address, or setup a irc.domain.com DNS [COLOR=Blue]Can I use a subdirectory like "irc.mysite.com/irc"?[/COLOR][/COLOR]
    sid = "ircd";[COLOR=Red]     <--- changed[/COLOR] [COLOR=Blue]So the SID doesn't have to be letter-number-number (like "A35" or similar, as suggested in the original conf file)?[/COLOR]
> 
** listen** {
    host = "bind.ip.address";[COLOR=Red]     <--- ip address you wanted to bind to[/COLOR] [COLOR=Blue]Would that be the IP address of the domain/server that the IRCd is installed on?[/COLOR]
    host = "bind.ip.address";[COLOR=Red]     <--- "      " [/COLOR][COLOR=Blue]Should I change this to the same IP address 2 lines up (1 line up)?[/COLOR]
    host = "3ffe:1234:a:b:c::d";[COLOR=Red]     <--- "ipv6      "[/COLOR] [COLOR=Blue]Will I need to retrieve the ipv6 version of my domain's/server's IP address (that the IRCd is installed on) and insert that in here?[/COLOR]
 > 
**operator** {
    user = "*@127.0.0.1";[COLOR=Red]     <--- only if you connect from 127.0.0.1 or localhost, on the box, and specific the hostname in your irc client [COLOR=Blue]This part is confusing. :-\[/COLOR][/COLOR][COLOR=Blue] Should I just leave this part alone?[/COLOR]
> 
** connect** { [COLOR=Blue]<--- Would I need to change the passwords in this section or just leave this part alone?[/COLOR]
    send_password = "password";[COLOR=Red]     <--- Leave this alone?[/COLOR]
    accept_password = "anotherpassword";[COLOR=Red]     <--- And this?[/COLOR]
 > 
**connect** {[COLOR=Red]     <--- Connecting remote server/leaf [COLOR=Blue](Another confusing section) :-\[/COLOR][/COLOR][COLOR=Blue] And not sure what "leaf" is.[/COLOR]
    name = "encrypted.auth.example";
    host = "some.host.somewhere";
    port = 6667;
    flags = cryptlink;
    rsa_public_key_file = "etc/remote.server.keyfile";
#    cipher_preference = "BF/168";
};
> 
**connect** "ipv6.some.server" {[COLOR=Red]     <--- example to link in a remote ipv6 server[/COLOR] [COLOR=Blue]Leave this alone also? Or change the "password" stuff/etc.?[/COLOR]
    host = "3ffd:dead:beef::1";
    send_password = "password";
    accept_password = "password";
    port = 6666;
    aftype = ipv6;
    class = "server";
};
 > 
**glines** {
    user = "god@I.still.hate.packets";[COLOR=Red]     <--- this is a gline block, are you trying to gline that user/vhost?[/COLOR] [COLOR=Blue]This line was default to the original example ircd.conf file. I figured just leave it as is. (?)[/COLOR]
 Thanks. :)

---

### Post by Th3Professor on 2010-01-13
<bump>

---

### Post by Th3Professor on 2010-01-14
Does anyone have any experience with setting up ircd.conf files (IRC server configuration files)?

I think I'm pretty close to getting things set up in the config file (see previous post with questions on that). I tried making some fresh changes to the file and running ircd again and although it was running in the background I was unable to connect to it via irc client. :(

---

### Post by Th3Professor on 2010-01-15
Does anyone have any experience with setting up ircd.conf files (IRC server configuration files)?

---

### Post by Th3Professor on 2010-01-16
<ferris bueller>
"...anyone? ...anyone?"

---

### Post by Th3Professor on 2010-01-17
Bump for the previous posts - questions about server setup.

Does anyone out there in the realm of "ubuntu-net" have any understanding of configuration files?

I'd like to get the ircd.conf file setup but am hitting a roadblock. Not sure why it's not working right now.

Thanks!

---

### Post by Th3Professor on 2010-01-18
Ah, the help has stopped :( ...can anyone help with the configuration of an ircd.conf file?

---

### Post by Th3Professor on 2010-01-19
Bummer... either not very many people on these forums have any ideas on ircd configs, or people do and they don't care to help, or people just haven't seen this topic. :( ...have tried other sources, including some IRC chats, but getting pretty much the same kind of results from other sources as here. Bummer.

---

