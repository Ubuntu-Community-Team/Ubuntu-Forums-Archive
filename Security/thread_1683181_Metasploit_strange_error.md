---
title: "Metasploit strange error"
date: 2011-02-07
forum: Security
---

### Post by yeleek on 2011-02-07
For various reasons have chosen to install metasploit as per
[http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

When starting msfconsole getting this, msf seems to work ok, but never seen these messages before.  Any ideas?

Thanks

```

[-] Failed to connect to the database: could not connect to server: Connection refused
	Is the server running on host "127.0.0.1" and accepting
	TCP/IP connections on port 7175?
 {"adapter"=>"postgresql", "database"=>"msf3", "username"=>"msf3", "password"=>"0f4a6458", "host"=>"127.0.0.1", "port"=>7175, "pool"=>75, "timeout"=>5} ["/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/postgresql_adapter.rb:968:in `initialize'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/postgresql_adapter.rb:968:in `new'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/postgresql_adapter.rb:968:in `connect'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/postgresql_adapter.rb:217:in `initialize'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/postgresql_adapter.rb:37:in `new'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/postgresql_adapter.rb:37:in `postgresql_connection'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:223:in `new_connection'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:245:in `checkout_new_connection'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:188:in `block (2 levels) in checkout'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:184:in `loop'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:184:in `block in checkout'", "/opt/framework-3.5.1/ruby/lib/ruby/1.9.1/monitor.rb:201:in `mon_synchronize'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:183:in `checkout'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:98:in `connection'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_pool.rb:326:in `retrieve_connection'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_specification.rb:123:in `retrieve_connection'", "/opt/framework-3.5.1/msf3/lib/active_record/connection_adapters/abstract/connection_specification.rb:115:in `connection'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1271:in `columns'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1284:in `column_names'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1297:in `column_methods_hash'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1986:in `block in all_attributes_exists?'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1986:in `each'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1986:in `all?'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1986:in `all_attributes_exists?'", "/opt/framework-3.5.1/msf3/lib/active_record/base.rb:1842:in `method_missing'", "/opt/framework-3.5.1/msf3/lib/msf/core/model/workspace.rb:28:in `default'", "/opt/framework-3.5.1/msf3/lib/msf/core/db.rb:176:in `default_workspace'", "/opt/framework-3.5.1/msf3/lib/msf/core/db_manager.rb:167:in `connect'", "/opt/framework-3.5.1/msf3/lib/msf/ui/console/driver.rb:181:in `initialize'", "/opt/framework-3.5.1/msf3/msfconsole:125:in `new'", "/opt/framework-3.5.1/msf3/msfconsole:125:in `<main>'"]

                __.                       .__.        .__. __.
  _____   _____/  |______    ____________ |  |   ____ |__|/  |_
 /     \_/ __ \   __\__  \  /  ___/\____ \|  |  /  _ \|  \   __\
|  Y Y  \  ___/|  |  / __ \_\___ \ |  |_> >  |_(  <_> )  ||  |
|__|_|  /\___  >__| (____  /____  >|   __/|____/\____/|__||__|
      \/     \/          \/     \/ |__|


       =[ metasploit v3.5.2-beta [core:3.5 api:1.0]
+ -- --=[ 644 exploits - 328 auxiliary
+ -- --=[ 216 payloads - 27 encoders - 8 nops
       =[ svn r11713 updated 3 days ago (2011.02.04)

resource (/home/pentest/.msf3/msfconsole.rc)> db_driver postgresql
[*] Using database driver postgresql
resource (/home/pentest/.msf3/msfconsole.rc)> db_connect msf_user:passwordremoved@127.0.0.1:5432/msf_database
resource (/home/pentest/.msf3/msfconsole.rc)> db_workspace -a MyProject
[*] Added workspace: MyProject
```

---

### Post by hackertarget on 2011-02-07
I would check if you have postgres configured and running correctly.

[http://www.metasploit.com/redmine/projects/framework/wiki/Postgres_setup](http://www.metasploit.com/redmine/projects/framework/wiki/Postgres_setup)

netstat -anp | grep 5432

Should show you if postgres is running on localhost

---

### Post by yeleek on 2011-02-08
It is and metasploit works fine as I say.

I guess the question is, given this

resource (/home/pentest/.msf3/msfconsole.rc)> db_driver postgresql[*] Using database driver postgresql
resource (/home/pentest/.msf3/msfconsole.rc)> db_connect msf_user:passwordremoved@127.0.0.1:5432/msf_database
resource (/home/pentest/.msf3/msfconsole.rc)> db_workspace -a MyProject[*] Added workspace: MyProject

Which work, where is metasploit getting the other configuration it complains about at first (which appears incorrect).

Regards

---

### Post by EJeanmaire on 2011-02-09
> **yeleek said:**
> It is and metasploit works fine as I say.

I guess the question is, given this

resource (/home/pentest/.msf3/msfconsole.rc)> db_driver postgresql[*] Using database driver postgresql
resource (/home/pentest/.msf3/msfconsole.rc)> db_connect msf_user:passwordremoved@127.0.0.1:5432/msf_database
resource (/home/pentest/.msf3/msfconsole.rc)> db_workspace -a MyProject[*] Added workspace: MyProject

Which work, where is metasploit getting the other configuration it complains about at first (which appears incorrect).

Regards

It almost looks like it is giving your verbose mode... did you set anything like that?

---

### Post by miloshcrh on 2011-03-07
> **yeleek said:**
> It is and metasploit works fine as I say.

I guess the question is, given this

resource (/home/pentest/.msf3/msfconsole.rc)> db_driver postgresql[*] Using database driver postgresql
resource (/home/pentest/.msf3/msfconsole.rc)> db_connect msf_user:passwordremoved@127.0.0.1:5432/msf_database
resource (/home/pentest/.msf3/msfconsole.rc)> db_workspace -a MyProject[*] Added workspace: MyProject

Which work, where is metasploit getting the other configuration it complains about at first (which appears incorrect).

Regards

The config information should be in the properties.ini file located in root of the install directory.

Metasploit is setting up its own posgres install and database during the install. It isn't running on startup and Metasploit gets upset when you start it. you can ignore it (because you already have your external install working) or run

 *sudo /opt/framework-3.5.2/postgresql/scripts/ctl.sh start*

before starting the console. there is a little more detail here

[http://epichacktime.com/blog/metasploitposgresstartupissue/](http://epichacktime.com/blog/metasploitposgresstartupissue/)

---

