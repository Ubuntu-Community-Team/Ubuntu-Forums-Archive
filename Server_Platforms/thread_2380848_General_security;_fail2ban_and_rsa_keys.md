---
title: "General security; fail2ban and rsa keys"
date: 2017-12-22
forum: Server Platforms
---

### Post by micahpage on 2017-12-22
Im having a problem trying to setup a method to stop bruteforcing.

Our server has been hacked before and im sure it might of been a bruteforce method. 
**Then** I tried setting up fail2ban, but i get an error that says the log files are missing and every tutorial that i can find does not explain this in great detail...so im left confused.
```
metulburr ~/.ssh $ sudo service fail2ban start 
* Starting authentication failure monitor fail2ban                                                      WARNING 'actionstart' not defined in 'Definition'. Using default one: ''
WARNING 'actionstop' not defined in 'Definition'. Using default one: ''
WARNING 'actioncheck' not defined in 'Definition'. Using default one: ''
ERROR  No file(s) found for glob /var/log/sshd.log
ERROR  Failed during configuration: Have not found any log file for ssh-route jail
                                                                                                  [fail]
```


**Then** i decided to scrap that idea, and just drop connections if they attempt to log in too many times by changing the iptables

```
iptables -A INPUT -p tcp --dport PORTNUM -m state --state NEW -m recent --set --name SSH -j ACCEPT
iptables -A INPUT -p tcp --dport PORTNUM -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j LOG --log-prefix "SSH_brute_force "
iptables -A INPUT -p tcp --dport PORTNUM -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
```


But that doesnt seem to work as i can sit there an attempt to login as many times as i want without being restricted at all. 

**Then** i decided to just stop passwords altogether and use rsa keys. But i am not sure what key to put on the server and which key to put on my home computer. If you have numerous users do they all have to do this? Does each person use the same key? Or do they all have to have separate keys?

```
metulburr ~/.ssh $ ls
authorized_keys  id_rsa  id_rsa.pub  known_hosts

```
am i suppose to put id_rsa.pub in the servers authorized_keys? And put id_rsa on my home computer? Or vice-versa. What happens if i lose that key like the hard drive crashes or something, will i be out of luck trying to log on to the server then?

I went through this tut
[https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
but they dont really specify which /home* is the server and which is your home computer? So its confusing. And i sure dont want to disable password login, because i will probably lock myself out of the server.

---

### Post by darkod on 2017-12-23
You can't put the ACCEPT iptables rule before the DROP. I think that is why it doesn't work for you.

The rules I use (but I do not redirect anything into logs) are these:
```
-A INPUT -i ens3 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i ens3 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
```

And according to iptables -L -n -v there is dropped traffic by that rule as expected:
```
1163K   70M DROP       tcp  --  ens3   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 state NEW recent: UPDATE seconds: 60 hit_count: 4 TTL-Match name: SSH side: source mask: 255.255.255.255
```

My ACCEPT rule is after/under the rules listed above.

As for SSH keys, it goes from client machine to server. The key from the client machine has to be put on the server in .ssh/authorized_keys.
If using linux client, you can simply use ssh-copy-id (in ubuntu) to copy your key onto the server. Look for its syntax.
From windows you would have to create a key with puttygen (make sure it's in openssh format) and then copy it as text into a new line on the server .ssh/authorized_keys.

---

