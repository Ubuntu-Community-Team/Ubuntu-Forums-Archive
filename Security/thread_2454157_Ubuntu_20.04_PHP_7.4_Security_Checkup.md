---
title: "Ubuntu 20.04 PHP 7.4 Security Checkup"
date: 2020-11-23
forum: Security
---

### Post by andyuk2 on 2020-11-23
Hi everyone,

I'm going to be running PHP 7.4 on my web servers.
Here are the values I am changing in my PHP.ini file to improve security.

```
max_execution_time = 18000
max_input_time = 18000
memory_limit = 256M
post_max_size = 400M
cgi.fix_pathinfo=0
upload_max_filesize = 400M
max_file_uploads = 2
allow_url_fopen = Off
allow_url_include = Off
register_globals = Off
max_input_vars = 100
safe_mode = On
sql.safe_mode = On
session.save_path = lib/php-h2m3c
soap.wsdl_cache_dir = /var/lib/php-h2m3c/soap_cache
session.use_strict_mode = 1
session.cookie_httponly = 1
session.use_cookies = 1
session.use_only_cookies = 1
session.use_trans_sid = 0
session.name = custom_session_id
session.cookie_secure = 1
session.referer_check = domain.com
session.hash_function = sha512
session.bug_compat_42 = 0
session.bug_compat_warn = 0


disable_functions = 
_getppid,allow_url_fopen,allow_url_include,chgrp,chmod,chown,curl_exec,curl_multi_exec,diskfreespace,dl,exec,fpaththru,getmypid,getmyuid,highlight_file,ignore_user_abord,ini_set,lchgrp,lchown,leak,link,listen,parse_ini_file,passthru,pcntl_alarm,pcntl_async_signals,pcntl_exec,pcntl_fork,pcntl_get_last_error,pcntl_getpriority,pcntl_setpriority,pcntl_signal,pcntl_signal_dispatch,pcntl_signal_get_handler,pcntl_sigprocmask,pcntl_sigtimedwait,pcntl_sigwaitinfo,pcntl_strerror,pcntl_unshare,pcntl_wait,pcntl_waitpid,pcntl_wexitstatus,pcntl_wifcontinued,pcntl_wifexited,pcntl_wifsignaled,pcntl_wifstopped,pcntl_wstopsig,pcntl_wtermsig,php_uname,phpinfo,popen,posix,posix_ctermid,posix_getcwd,posix_getegid,posix_geteuid,posix_getgid,posix_getgrgid,posix_getgrnam,posix_getgroups,posix_getlogin,posix_getpgid,posix_getpgrp,posix_getpid,posix_getpwnam,posix_getpwuid,posix_getrlimit,posix_getsid,posix_getuid,posix_isatty,posix_kill,posix_mkfifo,posix_setegid,posix_seteuid,posix_setgid,posix_setpgid,posix_setsid,posix_setuid,posix_times,posix_ttyname,posix_uname,proc_close,proc_get_status,proc_nice,proc_open,proc_terminate,putenv,set_time_limit,shell_exec,show_source,source,system,tmpfile,virtual



```

Please let me know if I have missed anything, or anything doesn't look quite right.

Thanks for your help,
Andy

---

### Post by DuckHook on 2020-11-24
Please use only default fonts and formatting when posting to the forums. Odd fonts are especially problematic when used within code tags.

---

### Post by SeijiSensei on 2020-11-25
The only security modification I routinely make to PHP is to set the default upload directory. Otherwise I use the stock defaults. Have never had an intrusion via PHP in some twenty years. Most of my web sites don't permit the web server "user" to write into any of its directories. Rather than worrying about these settings, I'd spend the time making sure your code is secure. Things like restricting inputs to only valid values, and scanning them for attempted hacks, are more important than these settings.

---

