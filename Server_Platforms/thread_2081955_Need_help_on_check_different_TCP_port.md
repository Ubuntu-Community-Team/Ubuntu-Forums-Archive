---
title: "Need help on check different TCP port"
date: 2012-11-08
forum: Server Platforms
---

### Post by veesyndicate on 2012-11-08
hai guys. I need help on checking certain tcp port on nagios. I just use this command to checking port 902. But the error appear when i try to validate. I just figure myself, but it did not work. Need guide. Thanks 

 define service {
        use                     generic-service
        host_name               ESX10,ESX11
        service_description     ISS-RealSecure
        check_command           check_tcp -p 902
     }

---

### Post by koenn on 2012-11-08
your check_command in the service def should look something like
```
 check_command     check_tcp!902 
```



this refers/should refer to a command definition (elsewhere in your nagios conf files, maybe in /etc/nagios-plugins/config/tcp_udp.cfg), something like
```

command_name	check_tcp
command_line   <path to plugin> -p $ARG1$ <...> 

```

see also [http://users.telenet.be/mydotcom/howto/nagios/commands.html](http://users.telenet.be/mydotcom/howto/nagios/commands.html)

---

### Post by veesyndicate on 2012-11-08
> **koenn said:**
> your check_command in the service def should look something like
```
 check_command     check_tcp!902 
```



this refers/should refer to a command definition (elsewhere in your nagios conf files, maybe in /etc/nagios-plugins/config/tcp_udp.cfg), something like
```

command_name	check_tcp
command_line   <path to plugin> -p $ARG1$ <...> 

```

see also [http://users.telenet.be/mydotcom/howto/nagios/commands.html](http://users.telenet.be/mydotcom/howto/nagios/commands.html)

Thanks! it work! =) 
Yesterday i was thinking about define new services in command.cfg for every TCP port that need to be monitor. If i define one by one,let say i have 300 TCP port to be monitor, then need 300x to define new services. Thanks God, you saving me a lot of time.

---

### Post by veesyndicate on 2012-11-08
i have one other question,how do i check https (port 443) on ESX Server? i use check_tcp! 443 but message "CRITICAL - Socket timeout after 10 seconds" appear. If i use check_https, it will return missing plugin. i could understand that because there is no check https file in libexec directory. How do i check https?

---

