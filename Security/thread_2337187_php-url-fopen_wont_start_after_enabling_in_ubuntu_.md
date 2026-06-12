---
title: "php-url-fopen wont start after enabling in ubuntu 16.04"
date: 2016-09-15
forum: Security
---

### Post by hawk0072 on 2016-09-15
I have a problem setting fail2ban using the following settings in the config file:

[php-url-fopen]
enabled = true



And:

[mysqld-auth]
enabled = true
filter =  mysqld-auth


When I enable these two rules fail2ban wont restart.


I did read somewhere that php-url-fopen wasn't compatable with my version of ubuntu 16.04 but couldnt understand what the solution was as Im a newbie.


Any help/pointers would be very much appreciated.


Thanks

---

### Post by SeijiSensei on 2016-09-15
Why do you care about controlling php-url-fopen anyway?  All that means is that certain PHP functions can use URLs the same way they use local files, e.g.,
```
$uf=fopen("http://ubuntuforums.org","r");
```
That creates a pointer to this site's front page and lets you read the contents of that page with commands like fread().

If removing it from fail2ban makes things work, just do that.  You don't really need to control php-url-fopen unless you have dodgy PHP applications running that request stuff from all over the Internet.  And if you do have such dodgy applications, you have bigger problems than enabling url-fopen.

---

### Post by hawk0072 on 2016-09-15
I was following one of digital oceans tutorials and it included enabling php-url-fopen.

Im no programmer so dont even know what it does to be honest.
But thanks for the tip

---

### Post by Habitual on 2016-09-15
> **hawk0072 said:**
> I was following one of digital oceans tutorials and it included enabling php-url-fopen.

Im no programmer so dont even know what it does to be honest.
But thanks for the tip

Post the entirety of the php-url-fopen jail please.
What link do you have for a reference?

> **hawk0072 said:**
> 
```
[php-url-fopen]
enabled = true
```

And:
```

[mysqld-auth]
enabled = true
filter = mysqld-auth
```
When I enable these two rules fail2ban wont restart.

Edit: If that IS the [php-url-fopen] and [mysql-auth] jails, they are sadly and woefully incomplete.
Copy /etc/fail2ban/jail.conf to /etc/fail2ban/jail.local and make your edits in /etc/fail2ban/jail.local
```
sudo cp  /etc/fail2ban/jail.conf   /etc/fail2ban/jail.local
```

The file(s) are littered with complete examples of working elements of a jail.
Not all examples with have all directives, but all the directives are in there.
Any directive not explicitly declared in the 
```
[jail_name]
enabled = true
...
...
``` will use the 
[DEFAULT]
values from  /etc/fail2ban/jail.local (first) and  /etc/fail2ban/jail.conf (read second if .local does exist, else first.

Only put enabled jails in /etc/fail2ban/jail.local is my advice.

if it doesn't start, I suggest as root
```
less /var/log/fail2ban.log
``` and see what's up.

Here's the jail in it's entirety from  /etc/fail2ban/jail.conf 
```
[php-url-fopen]

enabled = false
port    = http,https
filter  = php-url-fopen
logpath = /var/www/*/logs/access_log
```

I suggest this for yours in  /etc/fail2ban/jail.local
```
[php-url-fopen]

enabled = true 
port    = http,https
filter  = php-url-fopen
logpath = /var/www/*/logs/access_log
```

Yours is missing some directives.
Please read the liberally documented file at  /etc/fail2ban/jail.conf

Good Luck.

---

### Post by hawk0072 on 2016-09-15
The jail file contains the following:



```

[Definition]


failregex = ^<HOST> -.*"(GET|POST).*\?.*\=http\:\/\/.* HTTP\/.*$


ignoreregex = 

```

Os Version is: Ubuntu Server 16.04
Unsure of fail2ban version (0.9.0 release) - but its the latest using apt-get install fail2ban


Jail info as below:

```

[php-url-fopen]


enabled = true
port    = http,https
filter  = php-url-fopen
logpath = %(apache_access_log)s
maxretry = 1


```

Nothing mentioned in log using [COLOR=#000000][FONT=Ubuntu Mono]less /var/log/fail2ban.log[/FONT][/COLOR]


Thanks

---

### Post by hawk0072 on 2016-09-15
I also added the line below to the php-url-fopen jail

```

[php-url-fopen]


enabled = true
port    = http,https
filter  = php-url-fopen
logpath = %(apache_access_log)s
maxretry = 1
action = iptables-multiport[name=PHP-fopen, port=&#8221;http,https&#8221;, protocol=tcp]

```

And for the mysqld

```


[mysqld-auth]
enabled = true
filter =  mysqld-auth
port     = 3306
logpath  = %(mysql_log)s
maxretry = 5

```

---

### Post by SeijiSensei on 2016-09-15
So what is the purpose of jailing php-url-fopen?  What exploits is it supposedly protecting against?  I still don't see any reason for this.  

Suppose, for instance, I wrote a PHP script that went to a weather page, opened it with fopen(), and extracted the temperature data from the page.  Where's the security hole in that?  (I've done that very thing in the past.)

I could see a problem if you wrote a script that accepted a random URL in the request like:
```
http://www.example.com/?stupid_script.php?url=https://ubuntuforums.org
```
but any competent developer would never do that since it is so vulnerable to exploitation.  Anyone stupid enough to write a script like that isn't going to be running fail2ban.

---

### Post by Habitual on 2016-09-15
> **hawk0072 said:**
> The jail file contains the following:
```

[Definition]
failregex = ^<HOST> -.*"(GET|POST).*\?.*\=http\:\/\/.* HTTP\/.*$


ignoreregex = 

```
 That's the filter?  See /etc/fail2ban/filter.d/php-url-fopen.conf and it should be exactly as this [3 year-old .conf]("https://github.com/fail2ban/fail2ban/blob/master/config/filter.d/php-url-fopen.conf")

So, if that is the same, the I have issue with 
[COLOR=#ff0000]logpath = %(apache_access_log)s[/COLOR]
and I suggest ```
*logpath = /var/www/*/logs/access_log*
``` instead. Just my advice. 
I haven't used 0.9.x too much, but fortunately, f2b doesn't change that much from ver. to ver. </opinion>
Filters get improved a lot.

> **hawk0072 said:**
> 
Os Version is: Ubuntu Server 16.04
Unsure of fail2ban version (0.9.0 release) - but its the latest using apt-get install fail2ban
 Glad to hear it. :) So glad.

> **hawk0072 said:**
> Nothing mentioned in log using less /var/log/fail2ban.log

**Set loglevel to DEBUG**
```
fail2ban-client set loglevel 4
```
less /var/log/fail2ban.log
examine/search
tail -f /var/log/fail2ban.log will poll the files "end-of-file" continually.
ctrl+c cancels tail -f

**set loglevel to INFO** # Default
```
fail2ban-client set loglevel 3
```
If you use fail2ban-client in this manner, there is no need to edit /etc/fail2ban/jail.local to change INFO loglevel to DEBUG.

tail -f if you like.

Let is know.

Subscribed with interest.

---

### Post by hawk0072 on 2016-09-15
[COLOR=#000000][B]SeijiSensei

[/B][/COLOR]Im not a developer, far from it. I have just started learning and beginning with css so I have a long way to go.

I am just following what seem to be good instructions to lock down as far as possible a VPS.

The instructions I am referring to state:

[COLOR=#000000][FONT=proxima-nova]Lastly, if you are using Apache with PHP, you may want to enable the [php-url-fopen] jail, which blocks attempts to use certain PHP behavior for malicious purposes. You will likely have to change the logpath directive to point the correct access log location (on Ubuntu, the default location is /var/log/apache2/access.log). 

[/FONT][/COLOR]After I have learned a little and configured the vps as much as possible I plan to have a professional check it over. But Im not there yet.

---

### Post by hawk0072 on 2016-09-15
[COLOR=#000000]**Habitual**[/COLOR]
Yes thats the filter.

They're the same.

I just removed the commented stuff because this site wouldn't let me post the full code. Probably because of the html link. So I just left the active stuff.

The actual path to access.log is: /var/log/apache2/access.log

But that still doesn't allow fail2ban to restart.

I get an invalid log level error when I try to change the log level to 4.

ERROR  NOK: ('Invalid log level',)
Invalid log level

Il take another look in the morning.

Thanks for the pointers.

---

### Post by hawk0072 on 2016-09-16
I actually managed to get the php-url-fopen jail running...

The problem was that there was another jail by the same name in the jail.conf file.

```

[php-url-fopen]


port    = http,https
logpath = %(nginx_access_log)s
          %(apache_access_log)s

```

My bad.

So now the question really becomes is the code I am using now correct.

Whilst trying to fix the not restarting issue I found one post that said:

*The fail2ban doesnt work without adding an action to the  jail.*

He added this line after the maxretry lines.

```

action = iptables-multiport[name=PHP-fopen, port=&#8221;http,https&#8221;, protocol=tcp]

```

Not sure what that line does, or whether it is needed in the jail file?

Id appreciate any suggestions as I dont want to actually try adding it as it may change the iptables which I am not comfortable with until I know what is happening with that code.

Thanks again for the help. Much appreciated.

---

### Post by Habitual on 2016-09-16
> **hawk0072 said:**
> I actually managed to get the php-url-fopen jail running...

The problem was that there was another jail by the same name in the jail.conf file.
That would do it. Good Job, and Well Done.
new command for you:
```
fail2ban-client status php-url-fopen
```

---

### Post by hawk0072 on 2016-09-16
> **Habitual said:**
> That would do it. Good Job, and Well Done.
new command for you:
```
fail2ban-client status php-url-fopen
```

Nice, thanks for that. Hope the status stays at zero.
Much appreciated

---

### Post by Habitual on 2016-09-16
> **hawk0072 said:**
> Nice, thanks for that. Hope the status stays at zero.
Much appreciated
I don't.
Zero means your filter may be having issues.
or fail2ban has been restarted, or....
Have you manually checked the filter?

You can using 
```
fail2ban-regex /var/log/apache2/access.log /etc/fail2ban/filter.d/php-url-fopen.conf
```
and pay attention to the summary. 

Matches, or no?

---

