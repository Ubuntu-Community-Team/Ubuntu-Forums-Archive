---
title: "Systemd ExecStartPre with different credentials than ExecStart"
date: 2021-06-03
forum: Server Platforms
---

### Post by LHammonds on 2021-06-03
Is it possible to utilize different credentials (User/Group) for ExecStartPre and ExecStart?

The reason being is that I have an update/synchronization job that needs to happen when the service is not running and it seems like a perfect time to initiate the update just prior to whenever it starts regardless if it is on a set schedule or a restart after a failure or manually starting the service.

The credentials used to run the service is extremely minimal but the backup job needs extra rights to the backup location...which I do NOT want the running account to have.

Or am I just being dumb and should schedule another job that periodically stops the service, runs the backup and starts the service up and leave it at that?

LHammonds

---

### Post by scorp123 on 2021-06-03
> **LHammonds said:**
>  The reason being is that I have an update/synchronization job that needs to happen when the service is not running and it seems like a perfect time to initiate the update just prior to whenever it starts regardless if it is on a set schedule or a restart after a failure or manually starting the service.

The credentials used to run the service is extremely minimal but the backup job needs extra rights to the backup location...which I do NOT want the running account to have.

I'd use Ansible for that ...

```

---
- hosts: someserver
  become: true
  become_user: root

  tasks:

    - name: Stop service xyz
      systemd:
        name: myservice
        state: stopped

    - name: Do the update/backup thing
      copy:
        src: /path/to/scp/source/file.conf
        dest: /path/to/scp/target/dir/on/server/
        owner: serviceuser
        group: serviceuser
        mode: 0644

    - name: Start service xyz again
      # this gets executed as whatever user
      # is defined inside the service configuration
      # e.g. "serviceuser" or whatever
      # only the starting/stopping is done as "root"
      systemd:
        name: myservice
        state: started
        enabled: yes

```

Works for 1 server, 5 servers, 50 servers or 3000 servers. Ansible makes life so much easier.

---

### Post by LHammonds on 2021-06-03
I'd rather create a separate script that will run both processes with difference credentials before bringing in a 3rd-party solution.  I was hoping there was a way in systemd to handle this.

Would it be stupid to start the service under the more privileged account that can SU into the low-rights account as part of the ExecStart?

Example:
```

ExecStartPre=/var/scripts/prod/backup.sh
ExecStart=/usr/bin/su --command="/var/scripts/prod/service.sh" serviceuser
User=backupuser
Group=backupgroup

```

---

### Post by Tadaen_Sylvermane on 2021-06-13
[https://fedoramagazine.org/systemd-unit-dependencies-and-order/](https://fedoramagazine.org/systemd-unit-dependencies-and-order/)

Don't try to do it in a single service? I don't know much about anything admittedly but I can't help but think that one of the systemd hang ups people have is it's not as easy to put everything into a single service. Services that depend on services is a different way of thinking.

Make one require and after the other giving each the proper group / user declarations?

service 1

```
[Unit]
After=network.target

[Service]
ExecStart=/var/scripts/prod/backup.sh
User=backupuser
Group=backupgroup
```

service 2

```
[Unit]
Wants=service1.service
After=service1.service

[Service]
ExecStart=/var/scripts/prod/service.sh
# unsure if you need this
User=root
Group=root
```

---

### Post by MAFoElffen on 2021-06-13
> **LHammonds said:**
> Is it possible to utilize different credentials (User/Group) for ExecStartPre and ExecStart? ... LHammonds
I found this example for you...
```
[Unit]Description=Startup Thing


[Service]
Type=oneshot
ExecStart=/usr/bin/python3 -u /opt/thing/doStartup
WorkingDirectory=/opt/thing
StandardOutput=journal
User=thingUser
# Make sure the /run/thing directory exists
PermissionsStartOnly=true
ExecStartPre=-/bin/mkdir -p /run/thing
ExecStartPre=-/bin/chown thingUser /run/thing
ExecStartPre=-/bin/chmod 700       /run/thing



[Install]
WantedBy=multi-user.target

```
Note: For reference on directive documentation, use man serviced.directive ExecStartPre is documented in man systemd.service.

So in this example, the ExecStart is run by User "thingUser". The 4 ExecStartPre directives are run by root.

Note than in the example there is a "-" character. The ExecStartPre commands will commence serially, one after the other's end. If not prefixed by "-", then on failure, the unit will exit out with an error code, without any other processing. The "-" allows failure (such as the directory already being there). ExecStartPre is not meant for long running processes, at least as it is documented. It says that all forked processes invoked via ExecStartPre will be killed by the next service process starts... but if you are not forking the processes, they run serially so...

ExecStartPost will run directives after ExecStart finishes, at service end. Good for "clean-up" operations.

Additional to that, there's two "OTHER" ways to do that...

The first is to use one of the prefixes listed in the Execution prefix table in man systemd.service. Also contained in that table is notes on User, Group, SupplementaryGroup, DynamicUser, and elevated privilege's.

Second is to kick off the process via
```

ExecStartPre=/usr/bin/runuser -u username command_argument

```
Just a few ideas and options.

---

