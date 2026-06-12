---
title: "mysql-admin crashes (permissions error?)"
date: 2006-09-14
forum: Server Platforms
---

### Post by atraeyu on 2006-09-14
I installed mysql-admin: sudo apt-get mysql-admin

I've edited my /etc/mysql/my.cnf file so that:
*bind-address = 10.254.0.101* (my internal static ip)

When I load up mysql-admin: *mysql-admin*
The GUI pops right up.  Server hostname is localhost, username root.  Corresponding password.

I hit connect, it connects! Perfect.
I click on Service Control tab, no problem.  I click "Stop the Server" and get the following  message:
> Stopping MySQL database server: mysqldcat: /var/run/mysqld/mysqld.pid: Permission denied
...failed.
Could not open required defaults file: /etc/mysql/debian.cnf
Fatal error in defaults handling. Program aborted
Killing MySQL database server by signal: mysqldmysqld(4495): Operation not permitted
mysqld: no process killed


I can then click on ANY of the other tabs EXCEPT **User Administration**.  When I click on that tab, it displays the message "Retrieving Data from MySQL ..." at the bottom of the window, but it just sits there.  I have to force quit, everytime.

When I go back to the console, i see the following text:
> atraeyu@akira:~$ mysql-admin
Warning: The option old_passwords is not known. Please file a bug report if this  is a valid option.
Warning: The option expire-logs-days is not known. Please file a bug report if t his is a valid option.
Warning: The option skip-bdb is not known. Please file a bug report if this is a  valid option.

** (mysql-admin:6673): CRITICAL **: void MGFileBrowserList::get_row_object(const  Gtk::TreeIter&, std::string&): assertion `iter' failed
Killed


So, any idea what I'm doing wrong?  Is there something I need to configure in mysql-admin?  Thanks ...

---

### Post by lamego on 2006-09-14
About the permission denied for the start/stop operations, you will need to run mysql-admin with root: sudo mysql-admin

I have the same problem with User Administration panel.

I would recommend using phpmyadmin instead.

---

