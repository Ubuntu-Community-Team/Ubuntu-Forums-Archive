---
title: "Nextcloud, Apache &amp; Letsencrypt in Ubuntu 18.04 server"
date: 2020-05-22
forum: Server Platforms
---

### Post by ptdanpin on 2020-05-22
[FONT=arial]From the beginning of my setup I have been having probmles with obtaining the certificate for nextcloud from time to time. In the hardest cases I reinstall Ubuntu all the way, but it is a lot of work. I have a plex server, samba and a retroarch setup at the same time.
A couple of days the issue ocurred again. When running[/FONT] "sudo nextcloud.enable-https lets-encrypt" 
[FONT=arial]
The result is [/FONT]

```
2020-05-22 19:11:11,452:DEBUG:certbot.main:certbot version: 0.33.1
2020-05-22 19:11:11,453:DEBUG:certbot.main:Arguments: ['--text', '--config-dir', '/var/snap/nextcloud/current/certs/certbot/config', '--work-dir', '/var/snap/nextcloud/current/certs/certbot/work', '--logs-dir', '/var/snap/nextcloud/curr$2020-05-22 19:11:11,454:DEBUG:certbot.main:Discovered plugins: PluginsRegistry(PluginEntryPoint#manual,PluginEntryPoint#nextcloud:webroot,PluginEntryPoint#null,PluginEntryPoint#standalone,PluginEntryPoint#webroot)
2020-05-22 19:11:11,499:DEBUG:certbot.log:Root logging level set at 20
2020-05-22 19:11:11,501:INFO:certbot.log:Saving debug log to /var/snap/nextcloud/current/certs/certbot/logs/letsencrypt.log
2020-05-22 19:11:11,502:DEBUG:certbot.plugins.selection:Requested authenticator webroot and installer None
2020-05-22 19:11:11,518:DEBUG:certbot.plugins.selection:Single candidate plugin: * webroot
Description: Place files in webroot directory
Interfaces: IAuthenticator, IPlugin
Entry point: webroot = certbot.plugins.webroot:Authenticator
Initialized: <certbot.plugins.webroot.Authenticator object at 0x7f13b54709d0>
Prep: True
2020-05-22 19:11:11,519:DEBUG:certbot.plugins.selection:Selected authenticator <certbot.plugins.webroot.Authenticator object at 0x7f13b54709d0> and installer None
2020-05-22 19:11:11,520:INFO:certbot.plugins.selection:Plugins selected: Authenticator webroot, Installer None
2020-05-22 19:11:11,537:DEBUG:certbot.main:Picked account: <Account(RegistrationResource(body=Registration(status=None, terms_of_service_agreed=None, agreement=None, only_return_existing=None, contact=(), key=None, external_account_bind$2020-05-22 19:11:11,539:DEBUG:acme.client:Sending GET request to https://acme-v02.api.letsencrypt.org/directory.
2020-05-22 19:11:11,547:DEBUG:urllib3.connectionpool:Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org:443
2020-05-22 19:11:11,791:DEBUG:certbot.log:Exiting abnormally:
Traceback (most recent call last):
  File "/snap/nextcloud/20498/bin/certbot", line 8, in <module>
    sys.exit(main())
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/certbot/main.py", line 1364, in main
    return config.func(config, plugins)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/certbot/main.py", line 1233, in certonly
    le_client = _init_le_client(config, auth, installer)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/certbot/main.py", line 611, in _init_le_client
    return client.Client(config, acc, authenticator, installer, acme=acme)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/certbot/client.py", line 262, in __init__
    acme = acme_from_config_key(config, self.account.key, self.account.regr)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/certbot/client.py", line 47, in acme_from_config_key
    return acme_client.BackwardsCompatibleClientV2(net, key, config.server)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/acme/client.py", line 830, in __init__
    directory = messages.Directory.from_json(net.get(server).json())
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/acme/client.py", line 1168, in get
    self._send_request('GET', url, **kwargs), content_type=content_type)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/acme/client.py", line 1117, in _send_request
    response = self.session.request(method, url, *args, **kwargs)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/requests/sessions.py", line 533, in request
    resp = self.send(prep, **send_kwargs)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/requests/sessions.py", line 646, in send
    r = adapter.send(request, **kwargs)
  File "/snap/nextcloud/20498/lib/python2.7/site-packages/requests/adapters.py", line 514, in send
    raise SSLError(e, request=request)
SSLError: HTTPSConnectionPool(host='acme-v02.api.letsencrypt.org', port=443): Max retries exceeded with url: /directory (Caused by SSLError(SSLError("bad handshake: Error([('SSL routines', 'tls_process_server_certificate', 'certificate $2020-05-22 19:11:11,794:ERROR:certbot.log:An unexpected error occurred:
```


[FONT=arial]Been trying to solve the issu by myself and learned already quite a bit, but got nowhere. Got the information somewhere that the problem was apache, and yes, it does not run because of a por problem. Chaged it listening port to 8080 and it runs now. I cannot obtain the certificate for nextcloud regardless.


I have installed Ubuntu 18 server in a VM machine. In the instalation when selecting the nextcloud snap app, it will run smoothly. I get the certificate and all. If I select to install nextcloud after the complete Ubuntu instalation, I run into problems.

I am begining to loose my mind. Starting to believe in ghosts. #-o](*,)

Help or some pointers please. I am really committed to solve the issue the hard way this time.[/FONT]

---

### Post by LHammonds on 2020-05-22
I do not use snaps so I won't be of much help but is that "enable-https" command supposed to be used in just the initial creation of the SSL?  Is there a renewal command?  Is there a command that allows you to do a dry-run to see if it will renew the certs you have BEFORE trying to do it for real?

I did a quick look via good on snap + ssl but they were all VERY basic tutorials that only showed how to "enable" the SSL for the first time...never saw an example of how to renew or if enabling the ssl also setup a schedule that checks for renewal twice a day like a normal install does.

LHammonds

---

### Post by ptdanpin on 2020-05-22
> **LHammonds said:**
> I do not use snaps so I won't be of much help but is that "enable-https" command supposed to be used in just the initial creation of the SSL? 

It is intended to be in the initial creation only. There are a couple of commands using "nextcloud." like mysql related and export/import. Nothing to renew.

 > **LHammonds said:**
> Is there a renewal command?  Is there a command that allows you to do a dry-run to see if it will renew the certs you have BEFORE trying to do it for real?

LHammonds

From what I have seen until now, to renew the certificate a crontab must be done with "certbot renewal" command. Nothing I have tried until now. 

You question got me reading more posts. It seems everytime there is a snap update this happens. Those posts talk about apache server. Has I told already, my apache server is running with port 8080 (listen) because it also wasn't working properly.

I thank you for your reply and time

---

### Post by LHammonds on 2020-05-22
From my limited knowledge of snaps, they are supposed to be completely self-contained.  Do they package apache and mysql inside the snap?  If you had 3 different web-based snaps, does that mean 3 different apaches and databases are running?

If problems happen at update time, could the update be wiping the old info and replace it...thus requiring a re-setup?

LHammonds

---

### Post by ptdanpin on 2020-05-23
> **LHammonds said:**
> From my limited knowledge of snaps, they are supposed to be completely self-contained.  Do they package apache and mysql inside the snap?  If you had 3 different web-based snaps, does that mean 3 different apaches and databases are running?

If problems happen at update time, could the update be wiping the old info and replace it...thus requiring a re-setup?

LHammonds

My thoughts exacly. I'd like to solve the issue and with it gather info on how it works.

I am trying this forum, do you know about other that can help? 

I will post it on letsencrypt forum to have more detailed information about the log.

---

### Post by SeijiSensei on 2020-05-23
I would dump the snaps and use the regular version of Apache, then install certbot from [https://certbot.eff.org/](https://certbot.eff.org/).  

In /etc/crontab, I have this line to renew the certs as needed:

```
43 03 1 * * root certbot-auto renew >> /var/log/apache2/certbot 2>&1 && systemctl restart apache2 > /dev/null 2>&1
```

This checks for renewals at 03:43 on the first of every month.  It logs the results to /var/log/apache2/certbot.  If the update check completes correctly, it restarts the Apache server.

---

### Post by LHammonds on 2020-05-23
If you install certbot directly on 18.04 or 20.04, it has its own sytemd timer that checks twice a day.

Here is [my article]("https://hammondslegacy.com/forum/viewtopic.php?p=850#p850") that covers it.

LHammonds

---

### Post by SeijiSensei on 2020-05-23
NIce. My servers run CentOS 6 so they're not using systemd. At the time I created them at Linode I didn't want to deal with that, so I stayed on an earlier release.

---

### Post by ptdanpin on 2020-05-24
Problem solved. I had Pi-Hole installed. When updated it returned to it's original port (80) without my knowledge.

It was messing things up. Even after unninstalling it, lighttpd.conf had remained in disk and changing configurations every time I rebooted. (Had problems when "sudo apt update").

Didn't care much about hard code fixing it. The lesson is learned and I seized the opportunity to upgrade to Ubunto Server 20.

Everything runs smoothly. I have chose to not install pi-hole because my main purpose was to avoid youtube adds, which I didn't manage to get it working consistently.

Thanks for your time.

---

