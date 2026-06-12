---
title: "syslog-ng 3.1.2-1~lucid1 not writing to daemon.log, syslog, messages, etc."
date: 2011-08-04
forum: Server Platforms
---

### Post by ghstridr on 2011-08-04
Running on lucid 10.04.2
syslog-ng loaded from backports

Using stock config, but added a few lines to tail some files and push them to a splunk server.
It won't log the system log messages, but it pushes the additional logs out that I added (s_nginx_*).
I commented out my config and looking at the debug output, it looks like it's not matching anything in the base/default config.

```
# First, set some global options.
options { long_hostnames(off); flush_lines(0); use_dns(no); use_fqdn(no);
          owner("root"); group("adm"); perm(0640); stats_freq(0);
          bad_hostname("^gconfd$");
};
########################
# Sources
########################
# This is the default behavior of sysklogd package
# Logs may come from unix stream, but not from another machine.
#
source s_src { unix-dgram("/dev/log"); internal();
             file("/proc/kmsg" program_override("kernel"));
};

# If you wish to get logs from remote machine you should uncomment
# this and comment the above source line.
#
#source s_net { tcp(ip(127.0.0.1) port(1000) authentication(required) encrypt(allow)); };



# Additional sources to monitor

destination d_remote { udp("10.170.230.60" , port(4957)); };

source s_nginx_20 { file ("/iw-deploy/log/access-client-internal.log" follow_freq(1)); };
source s_nginx_21 { file ("/iw-deploy/log/access-client.log" follow_freq(1)); };
source s_nginx_22 { file ("/iw-deploy/log/access-server.log" follow_freq(1)); };
source s_nginx_23 { file ("/iw-deploy/log/celeryd.log" follow_freq(1)); };
source s_nginx_24 { file ("/iw-deploy/log/error.log" follow_freq(1)); };
source s_nginx_25 { file ("/iw-deploy/log/installer.log" follow_freq(1)); };
source s_nginx_26 { file ("/iw-deploy/log/island_gen.log" follow_freq(1)); };
source s_nginx_27 { file ("/iw-deploy/log/persistence.log" follow_freq(1)); };
source s_nginx_28 { file ("/iw-deploy/log/sec.log" follow_freq(1)); };
source s_nginx_29 { file ("/iw-deploy/log/worship1.log" follow_freq(1)); };
source s_nginx_30 { file ("/iw-deploy/log/worship2.log" follow_freq(1)); };
source s_nginx_31 { file ("/iw-deploy/log/worship_ff1.log" follow_freq(1)); };
source s_nginx_32 { file ("/iw-deploy/log/worship_router.log" follow_freq(1)); };
source s_nginx_33 { file ("/iw-deploy/log/persistence.err" follow_freq(1) ); };
source s_nginx_34 { file ("/iw-deploy/log/client-errors.log" follow_freq(1) ); };

log { source(s_nginx_20); destination(d_remote); };
log { source(s_nginx_21); destination(d_remote); };
log { source(s_nginx_22); destination(d_remote); };
log { source(s_nginx_23); destination(d_remote); };

log { source(s_nginx_24); destination(d_remote); };
log { source(s_nginx_25); destination(d_remote); };
log { source(s_nginx_26); destination(d_remote); };
log { source(s_nginx_27); destination(d_remote); };
log { source(s_nginx_28); destination(d_remote); };
log { source(s_nginx_29); destination(d_remote); };
log { source(s_nginx_30); destination(d_remote); };
log { source(s_nginx_31); destination(d_remote); };
log { source(s_nginx_32); destination(d_remote); };
log { source(s_nginx_33); destination(d_remote); };
log { source(s_nginx_34); destination(d_remote); };

######
# destinations

# some standard log files
destination df_auth { file("/var/log/auth.log"); };
destination df_syslog { file("/var/log/syslog"); };
destination df_cron { file("/var/log/cron.log"); };
destination df_daemon { file("/var/log/daemon.log"); };
destination df_kern { file("/var/log/kern.log"); };
destination df_lpr { file("/var/log/lpr.log"); };
destination df_mail { file("/var/log/mail.log"); };
destination df_user { file("/var/log/user.log"); };
destination df_uucp { file("/var/log/uucp.log"); };
######
# destinations

# some standard log files
destination df_auth { file("/var/log/auth.log"); };
destination df_syslog { file("/var/log/syslog"); };
destination df_cron { file("/var/log/cron.log"); };
destination df_daemon { file("/var/log/daemon.log"); };
destination df_kern { file("/var/log/kern.log"); };
destination df_lpr { file("/var/log/lpr.log"); };
destination df_mail { file("/var/log/mail.log"); };
destination df_user { file("/var/log/user.log"); };
destination df_uucp { file("/var/log/uucp.log"); };

# these files are meant for the mail system log files
# and provide re-usable destinations for {mail,cron,...}.info,
# {mail,cron,...}.notice, etc.
destination df_facility_dot_info { file("/var/log/$FACILITY.info"); };
destination df_facility_dot_notice { file("/var/log/$FACILITY.notice"); };
destination df_facility_dot_warn { file("/var/log/$FACILITY.warn"); };
destination df_facility_dot_err { file("/var/log/$FACILITY.err"); };
destination df_facility_dot_crit { file("/var/log/$FACILITY.crit"); };

# these files are meant for the news system, and are kept separated
# because they should be owned by "news" instead of "root"
destination df_news_dot_notice { file("/var/log/news/news.notice" owner("news")); };
destination df_news_dot_err { file("/var/log/news/news.err" owner("news")); };
destination df_news_dot_crit { file("/var/log/news/news.crit" owner("news")); };

# some more classical and useful files found in standard syslog configurations
destination df_debug { file("/var/log/debug"); };

destination df_messages { file("/var/log/messages"); };

# pipes
# a console to view log messages under X
destination dp_xconsole { pipe("/dev/xconsole"); };

# consoles
# this will send messages to everyone logged in
destination du_all { usertty("*"); };


######
# filters

# all messages from the auth and authpriv facilities
filter f_auth { facility(auth, authpriv); };

# all messages except from the auth and authpriv facilities
filter f_syslog { not facility(auth, authpriv); };

# respectively: messages from the cron, daemon, kern, lpr, mail, news, user,
# and uucp facilities
filter f_cron { facility(cron); };
filter f_daemon { facility(daemon); };
filter f_kern { facility(kern); };
filter f_lpr { facility(lpr); };
filter f_mail { facility(mail); };
filter f_news { facility(news); };
filter f_user { facility(user); };
filter f_uucp { facility(uucp); };

# some filters to select messages of priority greater or equal to info, warn,
# and err
# (equivalents of syslogd's *.info, *.warn, and *.err)
filter f_at_least_info { level(info..emerg); };
filter f_at_least_notice { level(notice..emerg); };
filter f_at_least_warn { level(warn..emerg); };
filter f_at_least_err { level(err..emerg); };
filter f_at_least_crit { level(crit..emerg); };

# all messages of priority debug not coming from the auth, authpriv, news, and
# mail facilities
filter f_debug { level(debug) and not facility(auth, authpriv, news, mail); };

# all messages of info, notice, or warn priority not coming form the auth,
# authpriv, cron, daemon, mail, and news facilities
filter f_messages {
        level(info,notice,warn)
            and not facility(auth,authpriv,cron,daemon,mail,news);
};

# messages with priority emerg
filter f_emerg { level(emerg); };

# complex filter for messages usually sent to the xconsole
filter f_xconsole {
    facility(daemon,mail)
        or level(debug,info,notice,warn)

        or (facility(news)
                and level(crit,err,notice));
};


######
# logs
# order matters if you use "flags(final);" to mark the end of processing in a
# "log" statement

# these rules provide the same behavior as the commented original syslogd rules

# auth,authpriv.*                 /var/log/auth.log
log {
        source(s_src);
        filter(f_auth);
        destination(df_auth);
};

# *.*;auth,authpriv.none          -/var/log/syslog
log {
        source(s_src);
        filter(f_syslog);
        destination(df_syslog);
};

# this is commented out in the default syslog.conf
# cron.*                         /var/log/cron.log
#log {
#        source(s_src);
#        filter(f_cron);
#        destination(df_cron);
#};

# daemon.*                        -/var/log/daemon.log
log {
        source(s_src);
        filter(f_daemon);
        destination(df_daemon);
};

# kern.*                          -/var/log/kern.log
log {
        source(s_src);
        filter(f_kern);
        destination(df_kern);
};

# lpr.*                           -/var/log/lpr.log
log {
        source(s_src);
        filter(f_lpr);
        destination(df_lpr);
};

# mail.*                          -/var/log/mail.log
log {
        source(s_src);

        filter(f_mail);
        destination(df_mail);
};

# user.*                          -/var/log/user.log
log {
        source(s_src);
        filter(f_user);
        destination(df_user);
};

# uucp.*                          /var/log/uucp.log
log {
        source(s_src);
        filter(f_uucp);
        destination(df_uucp);
};

# mail.info                       -/var/log/mail.info
log {
        source(s_src);
        filter(f_mail);
        filter(f_at_least_info);
        destination(df_facility_dot_info);
};

# mail.warn                       -/var/log/mail.warn
log {
        source(s_src);
        filter(f_mail);
        filter(f_at_least_warn);
        destination(df_facility_dot_warn);
};

# mail.err                        /var/log/mail.err
log {
        source(s_src);
        filter(f_mail);
        filter(f_at_least_err);
        destination(df_facility_dot_err);
};

# news.crit                       /var/log/news/news.crit
log {
        source(s_src);
        filter(f_news);
        filter(f_at_least_crit);
        destination(df_news_dot_crit);
};

# news.err                        /var/log/news/news.err
log {
        source(s_src);
        filter(f_news);
        filter(f_at_least_err);
        destination(df_news_dot_err);
};


# news.notice                     /var/log/news/news.notice
log {
        source(s_src);
        filter(f_news);
        filter(f_at_least_notice);
        destination(df_news_dot_notice);
};


# *.=debug;\
#         auth,authpriv.none;\
#         news.none;mail.none     -/var/log/debug
log {
        source(s_src);
        filter(f_debug);
        destination(df_debug);
};


# *.=info;*.=notice;*.=warn;\
#         auth,authpriv.none;\
#         cron,daemon.none;\
#         mail,news.none          -/var/log/messages
log {
        source(s_src);
        filter(f_messages);
        destination(df_messages);
};

# *.emerg                         *
log {
        source(s_src);
        filter(f_emerg);
        destination(du_all);
};


# daemon.*;mail.*;\
#         news.crit;news.err;news.notice;\
#         *.=debug;*.=info;\
#         *.=notice;*.=warn       |/dev/xconsole
log {
        source(s_src);
        filter(f_xconsole);
        destination(dp_xconsole);
};

```

---

