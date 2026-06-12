---
title: "using localhost for offline development"
date: 2007-04-27
forum: Server Platforms
---

### Post by jammodotnet on 2007-04-27
Hiya.

I own a few domain names, one of which is [www.jammo.net](www.jammo.net)
I read elsewhere (forgot the link) that a user had set up his Ubuntu with LAMP + using virtual hosts, he does something like this:

[www.website.com](www.website.com) => his live website
[www.website.dev](www.website.dev) => his developmental OFFLINE website

I been reading up on [http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/) about how to do this.
So far, I've figured this part out:
```
httpd.conf

<VirtualHost *:80>
		ServerName www.jammo.dev
		ServerAlias domain.tld *.jammo.dev
		DocumentRoot /home/user/public_html/jammo.dev
</VirtualHost>
```

I suppose, what my 'goal' is, to enter the URL: [www.jammo.dev](www.jammo.dev) and it will show me my localhost directory '*/home/user/public_html/jammo.dev*'.
And enter URL: [www.jammo.net](www.jammo.net) and it will show my website.
But only I would be able to view [www.jammo.dev](www.jammo.dev)

I know it has lots to do with Virtual Hosts, it's pretty confusing since I'm not even certain I've got the above understood well.

---

### Post by [S|G] on 2007-04-28
Just a (maybe) silly question: did you point jammo.dev to your own machine on your /etc/hosts file?

---

### Post by jammodotnet on 2007-04-28
> **'[S|G] said:**
> Just a (maybe) silly question: did you point jammo.dev to your own machine on your /etc/hosts file?
remember how like in School, teachers would always say, "there's no such thing as a silly question".
well ... haha, i say the same thing.

yeah, i did this:
```
127.0.1.1	jammo.dev
```

actually, it ended up lookin like this:
```
127.0.0.1	localhost jammo-desktop
127.0.1.1	jammo-desktop
127.0.1.1	suncitystreetscene.dev
127.0.1.1	jammo.dev
```

suncitystreetscene.net is another domain i'd like to developer this way, thus the other entry there.

but since i'm quite a ways from getting all this perfected, i undid all my changes, and reverted all files to original status. untill i understand what i'm doing here.
i dont want to render my LAMP useless.

that would be catastrophic!! :-({|=

---

### Post by jammodotnet on 2007-04-28
actually, i just finished reading this short briefing: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F)

so for the time being (just learning mostly), i can access: /home/jammo/public_html/jammo.dev via [http://localhost/jammo.dev/](http://localhost/jammo.dev/)

---

### Post by [S|G] on 2007-04-28
Did you try to include the NameVirtualHost directive before the virtual host? it would be something like this:
```

    NameVirtualHost *

    <VirtualHost *>
    ServerName www.jammo.dev
    DocumentRoot /home/user/public_html/jammo.dev
    </VirtualHost>

```

Btw, nice blog :) That easyVMX seems to be really handy!

---

### Post by jammodotnet on 2007-04-28
ya think you can mention all the steps i need to take to get this done?
i REALLY dont want to F- this up again :(

oh, thanks for the blog compliment.
i run ExpressionEngine Core on jammo.net
and bought EE 1.5.2 for suncitystreetscene.net

suncitystreetscene is actually hosted on the same domain as jammo.net, as is another site.
all 3 will run off of ExpressionEngine, IF i can properly manage my offline development.

thats why i need 200% understanding of what i'm doing.
:)

---

### Post by [S|G] on 2007-04-28
I have just adjusted my own apache2 to use virtualhosts and make a quick test. It is now working with two virtualhosts (sg.homelinux.com and [www.diegolima.dev)](www.diegolima.dev)). Basically, this is my configuration:

```

NameVirtualHost *

<Virtualhost *>
ServerName sg.homelinux.com
DocumentRoot /home/diego/public_html

(lots of configurations here)

Options Indexes MultiViews FollowSymLinks
</Virtualhost>

<Virtualhost *>
Servername www.diegolima.dev
DocumentRoot /home/diego/public_html/files/public
</VirtualHost>

```

After doing that, I restarted my apache and everything was working. Are you still having trouble with your configuration?

---

