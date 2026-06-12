---
title: "Apache logging"
date: 2011-02-13
forum: Server Platforms
---

### Post by druhboruch on 2011-02-13
Could you advise me on how to properly setup rsyslog to log apache events to different log files.
I would like to separate events by the source: local network to one file and all the remaining events to the other.
Thanks.

---

### Post by SeijiSensei on 2011-02-14
You do it in the configurations for the various virtual hosts.  For example,

```

<VirtualHost *:80>
ServerName virtual1.example.com
TransferLog logs/combined_log-virtual1
ErrorLog    logs/error_log-virtual1

[etc.]
</VirtualHost>

<VirtualHost *:80>
ServerName virtual2.example.com
TransferLog logs/combined_log-virtual2
ErrorLog    logs/error_log-virtual2

[etc.]
</VirtualHost>


```

Requests for virtual1.example.com will be logged separately from requests for virtual2.example.com.

---

### Post by druhboruch on 2011-02-14
Thank you for your reply.
I know that I can log each virtual host to the separate file.

I would like to keep local and remote access events in the separate files.
If the server is accessed from 192.168.1.0 or loopback it should go to one file.
If the server is accessed from any other address it should go to another log file. 
I am sorry that my question was not clear.

---

### Post by SeijiSensei on 2011-02-15
I don't think there's any way to do what you want in real-time.  You can always grep the log files for IP address strings (assuming you don't have Apache resolve IP addresses to names before logging):

```

grep '127.0.0.1' /var/log/apache2/access_log > localhost_access
grep '192.168.1' /var/log/apache2/access_log > localnet_access

```

would pull the localhost and local network records.  

Another option is to use a log analyzer like [Analog]("http://www.analog.cx/").

---

### Post by druhboruch on 2011-02-15
> **SeijiSensei said:**
> I don't think there's any way to do what you want in real-time.  You can always grep the log files for IP address strings (assuming you don't have Apache resolve IP addresses to names before logging):



Thanks.
This is what I have been doing.

I was hoping that there was some better way.

---

