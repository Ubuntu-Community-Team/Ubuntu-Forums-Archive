---
title: "ssh help (lots of questions)"
date: 2011-03-23
forum: Security
---

### Post by flyingsliverfin on 2011-03-23
I want to set up a secure ssh server on my desktop. So far, I've installed the openssh-server package using apt-get. However, i read somewhere that it is more secure to change the port. So i edited the /etc/ssh/sshd_config "port 22" line to read "port 500".

My first question is, what does this do? 
And since I'm sitting behind a router, do i need to change the port forwarding for incoming connections (that are going to port 22) to forward to 500? or does that defy of the point of doing it in the first place.

Also how would I configure it to restrict remote access to a certain folder (maybe a separate user's directory would be better?)
One last thing (related to above): i only want my friends and i to log in/transfer files using a certain user, and then not be able to use sudo... I believe that i can restrict a certain user's ability to use sudo using the same kind of thing that makes only certain users administrators, correct?

im fine with using bash. Actually, I would prefer to use it! I feel like i learn 10x more that way
Oh and really last thing i've changed my computer's DHCP to static (outside of the DHCP range assigned to other comps so there are no conflicts) so the IP doesnt change... not sure if this actually does anything

---

### Post by dmizer on 2011-03-23
Moving the server's access port does very little for security.

Before you forward the ssh port through your firewall, you should disable password based logins and read up on how to secure the server with shared keys: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

One of the most common ways that Linux systems are compromised is through poorly secured SSH servers with username/password access.

---

### Post by deconstrained on 2011-03-23
If you're behind a router you don't even need to configure SSH for an unconventional port; you just forward from whatever port you want on the outside to 22 on the inside. The open port on the outside is what's important.

And yes, it is more secure to use an unconventional port, because brute-force SSH attackers will leave you alone; they don't have the time/resources to scan every host on every net for an open TCP port that responds to SSH requests. So they take the cookie-cutter approach by scripting password guess login attempts on port 22. If someone knows a username on your machine AND the port then you'll need to get down to business and use DenyHosts and other SSH intrusion-stoppers, but for the most part you'll be safe if you use a random port and disable root login (see 'man sshd_config' for details)

...But you'll want to use a port that is "unprivileged" --i.e. that isn't already dedicated to something else;
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Dynamic.2C_private_or_ephemeral_ports:_49152.E2.80.9365535](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Dynamic.2C_private_or_ephemeral_ports:_49152.E2.80.9365535)
Something up in the 50k range would work. 

Also, did I mention: disable root login?

---

### Post by amauk on 2011-03-23
Changing the port does little for security
It'll stop basic brute-force attacks, but it's security through obscurity

Better to have an active prevention in place
Check out denyhosts (it's in the repos)
It's a daemon that monitors /var/log/auth.log for incorrect SSH login attempts and bans IPs after x number of attempts

Far more secure than just changing the port

---

### Post by flyingsliverfin on 2011-03-24
Well stopping brute force is good enough for now :) I'm just trying to learn.

I've run into a prblem:
i changed the port to 49152 on both my router and /etc/ssh/sshd_config (for some reason it won't let me forward from 49152 to 22). But when i try ssh -p 49152 xxx it gives me:
Read from socket failed: Connection reset by peer

help?

any ideas on how to restrict remote access to a certain folder or user's directory?

---

### Post by deconstrained on 2011-03-25
> **flyingsliverfin said:**
> But when i try ssh -p 49152 xxx it gives me:
Read from socket failed: Connection reset by peer
Could be any number of things. Check /etc/hosts.allow, /etc/hosts.deny, and your firewall configuration (on both the local host and the router), to begin with.

> any ideas on how to restrict remote access to a certain folder or user's directory?
Set the permissions on user directories as you please to restrict/allow access. See the "DIR_MODE" variable in /etc/adduser.conf if you wish to have a default mode for all new users' home directories.

---

### Post by dmizer on 2011-03-25
> **flyingsliverfin said:**
> Well stopping brute force is good enough for now :) I'm just trying to learn.

You might want to reconsider that:
[http://www.google.com/#sclient=psy&hl=en&q=ssh+hacked+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=1fd3bc16a86a49f1](http://www.google.com/#sclient=psy&hl=en&q=ssh+hacked+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=1fd3bc16a86a49f1)

Opening your system to a direct connection to the internet is not something to take lightly.

---

### Post by Tabu.it on 2011-03-25
Use denyhosts to block SSH- brute force. 
[http://ubuntuforums.org/showthread.php?t=450853](http://ubuntuforums.org/showthread.php?t=450853)

I think also iptables could do the same.

---

### Post by CharlesA on 2011-03-25
> **dmizer said:**
> You might want to reconsider that:
[http://www.google.com/#sclient=psy&hl=en&q=ssh+hacked+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=1fd3bc16a86a49f1](http://www.google.com/#sclient=psy&hl=en&q=ssh+hacked+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=1fd3bc16a86a49f1)

Opening your system to a direct connection to the internet is not something to take lightly.
+1. I would suggest not allowing access to SSH directly from the internet if you are just learning.

There's a very good sticky on security [here]("http://ubuntuforums.org/showthread.php?t=510812").

I use [iptables]("http://bodhizazen.net/Tutorials/iptables") to limit bruteforce attacks, since it means I have one less service running.

---

### Post by bodhi.zazen on 2011-03-25
After running ssh servers for many years I would be of the opinion that the most important single thing you can do is to use keys and disable password authentication.

The problem with changing ports is that it adds very little to security. It stops script kiddies (as they are called), but you did that with keys, so changing the port does not really matter.

Changing the port is a placebo, it makes those who watch the logs feel as if they accomplished something more then quieting the logs.

The problem with denyhosts and fail2ban is that they introduce additional services which can also be a security risk and they can also result in a dos (or worse).

If you must, IMO, denyhosts is best if you are using only a ssh server, fail2ban is better with other services (ftp, http authentication, etc).

If you must, configure iptables, it is a few "simple" rules, takes as long to learn as it does to learn fail2ban or denyhosts (assuming you read the config file , which you should when it comes to security applications, lol).

If you do not want to learn iptables, use ufw and limit the ssh connections.

The problem with TCPWrapper (hosts allow/deny) is that you need to know the ipaddress you wish to allow. I would use tcpwrapper if this is known.

Alternates to all of the above include psad and fwsnort, both are light weight and cover more then just ssh, but with some of the same problems of denyhosts / fail2ban.

HTH

---

### Post by msandoy on 2011-03-25
I have to say, I'm a bit surprised about the attitude of the forum staff here regarding changing the ssh default port. I have a server myself, on a budget line, it has been running on a 2 Mbit SHDSL line for a few years. And while I was using default port 22, I had frequent connection problems to the internet with the other computers on my network. I can tell you that when your server is being attacked with 1500+ login requests per hour, your internet is going to suck big time. Change away from the default port. It might not do much for security, but it will make your internet life easier.
Denyhosts and random ports are a blessing.

---

### Post by dmizer on 2011-03-25
> **msandoy said:**
> I have to say, I'm a bit surprised about the attitude of the forum staff here regarding changing the ssh default port.

None of us are suggesting that it's not a good idea. All of us are suggesting that it's not even close to "good enough".

---

### Post by msandoy on 2011-03-25
As I said, "It might not do much for security." 
Back on track. OP, I suggest, since you are doing this as a learning experience, you should install logwatch to make the job of sifting through log files a bit easier. It might make you a bit paranoid in the beginning, but a healthy dose of paranoia never hurt anyone.
Ports in the very high numbers are sometimes assosiated with malware and filesharing traffic. Depending on your ISP, this might be restricted.

---

### Post by flyingsliverfin on 2011-03-26
wow I've attracted 3 forum staff to post :)

the read from socket failed fixed itself with a restart

---

### Post by deconstrained on 2011-03-26
> **flyingsliverfin said:**
> wow I've attracted 3 forum staff to post :)

the read from socket failed fixed itself with a restart
You need to restart the ssh daemon (at least) for configuration changes to take effect. That would explain why it was solved after restarting.

Also, the staff are giving good advice. Using IPtables to limit SSH requests per minute is a great additional security measure, and lessens the strain on the daemon and DenyHosts. Maybe overkill for a small home server, but worth looking into.

---

### Post by brian_p on 2011-03-26
> **msandoy said:**
> I have to say, I'm a bit surprised about the attitude of the forum staff here regarding changing the ssh default port. I have a server myself, on a budget line, it has been running on a 2 Mbit SHDSL line for a few years. And while I was using default port 22, I had frequent connection problems to the internet with the other computers on my network. I can tell you that when your server is being attacked with 1500+ login requests per hour, your internet is going to suck big time. Change away from the default port. It might not do much for security, but it will make your internet life easier.
Denyhosts and random ports are a blessing.

I sympathise with you if attempted logins to sshd impact on your internet use and would probably take similar measures to the ones you have in place if it were to happen to me. However, I am pleased to see the responses here debunk the "changing ssh default port increases security" claim. Many articles advocating it do so on this basis rather than focus on the annoyance factor.

What surprises me a bit is promoting ssh keys over a good password. There are advantages ssh keys have over password logins (their use in scripting, for example) but an 18 character password is hardly less secure than a ssh key.

---

### Post by CharlesA on 2011-03-26
> **brian_p said:**
> 
What surprises me a bit is promoting ssh keys over a good password. There are advantages ssh keys have over password logins (their use in scripting, for example) but an 18 character password is hardly less secure than a ssh key.

The main benefit of using keys over passwords is that they can't be bruteforced. If you've got a strong non-dictionary password, you should be fine.

Found a short pro/con list [here]("http://rongchaua.net/blog/ssh-password-vs-public-key/").

---

### Post by Doug S on 2011-03-26
For idenifying and temporarily (90 minutes in this example) blocking IP addresses that are trying brute force attacks on the SSH (secure shell) port, I have been using the following iptable rules for many years now:

```

# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```
 
Very rarely, an attacker will be trying many ports during the same attack. Notice that the DROP rule is not port specific, but will DROP every packet from the bad guy IP address.
 
While not required, but to reduce the permitted number of password attempts per connection, I also edit the sshd_config file and add the following:

```
 
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2

```
 
Note: there was a thread very similar to this one just over a month ago. The notes I put here are the similar to the ones I added in that thread.

---

### Post by brian_p on 2011-03-26
> **CharlesA said:**
> The main benefit of using keys over passwords is that they can't be bruteforced. If you've got a strong non-dictionary password, you should be fine.

Found a short pro/con list [here]("http://rongchaua.net/blog/ssh-password-vs-public-key/").

The page [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.digitalkingdom.org/rlp/tiki-index.php?page=SSH+Keys+Kinda+Suck") presents a more detailed argument from the point of view of a sys admin.

---

### Post by CharlesA on 2011-03-26
> **brian_p said:**
> The page [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.digitalkingdom.org/rlp/tiki-index.php?page=SSH+Keys+Kinda+Suck") presents a more detailed argument from the point of view of a sys admin.
Thanks for the link, it was a good read. :)

---

### Post by msandoy on 2011-03-26
Well, i stirred up a bit of discussion with my last post. Discussion is good, as long as we stay away from fist fighting.
As a long time user of weak passwords, I came across the (in my opinion) best solution for others like me (short term memory impaired), the password card. Can't remember witch thread I found it in.
[http://www.passwordcard.org/en](http://www.passwordcard.org/en)
I know you are not supposed to write down your password, but even if I lost the card, I doubt they would guess witch one of them I used.

---

### Post by brian_p on 2011-03-26
> **CharlesA said:**
> Thanks for the link, it was a good read. :)

I'm glad you got some enjoyment out of it; it was something I only came across today and, for myself, it resonates with my thinking on the use of ssh and basic security.

I can understand the use of ssh keys in a situation where the password is weak or suspected to be weak but if I were to choose one quote it would be:

> I'm of the opinion that ssh keys and passwords are about equal in terms of security; they both have their places. Neither is a panacea, and you are not committing security suicide by leaving either enabled.

I also like the interplay between the inbuilt security of a piece of software and the human factor, which is aluded to in the article. It is something people (myself included) may very well forget about.

---

### Post by CharlesA on 2011-03-26
That part definitely rings true.

---

### Post by flyingsliverfin on 2011-03-26
Right so now I've made a somewhat hidden user (because my parents sometimes use this computer, I don't want them messing with the ssh account), and restricted access to only that user and not mine or my parents or my brother's. Oh and i also turned up the logging to verbose to see what it looks like.

However, It's not working for some reason (the loggin in) because as soon as I log into ssh, it almost instantaneously  closes the connection. Why? There's nothing in the log either

---

### Post by cariboo on 2011-03-26
> **flyingsliverfin said:**
> Right so now I've made a somewhat hidden user (because my parents sometimes use this computer, I don't want them messing with the ssh account), and restricted access to only that user and not mine or my parents or my brother's. Oh and i also turned up the logging to verbose to see what it looks like.

However, It's not working for some reason (the loggin in) because as soon as I log into ssh, it almost instantaneously  closes the connection. Why? There's nothing in the log either

It sounds like you have permission issues. To check what is happening when you try to connect via ssh us the verbose option -v

```
ssh -v user@server
```

add more v's for more output.

---

### Post by flyingsliverfin on 2011-03-27
this is what the -v displays after my banner:

```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/joshua/.ssh/identity
debug1: Trying private key: /home/joshua/.ssh/id_rsa
debug1: Trying private key: /home/joshua/.ssh/id_dsa
debug1: Next authentication method: password
ssh@localhost's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux joshua-desktop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Sat Mar 26 21:05:57 2011 from localhost
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to localhost closed.
Transferred: sent 1744, received 2520 bytes, in 0.2 seconds
Bytes per second: sent 6990.9, received 10101.6
debug1: Exit status 1

```

---

### Post by bodhi.zazen on 2011-03-27
> **brian_p said:**
> The page [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.digitalkingdom.org/rlp/tiki-index.php?page=SSH+Keys+Kinda+Suck") presents a more detailed argument from the point of view of a sys admin.

Thanks for the link, it was a good read, but I would strongly disagree with the sweeping conclusions the author draws from his or her experience.

The article is long on opinions, and short on data. For example, in the "Remote Fun With sudo" section, the author claims the server was cracked by a stolen ssh key, and then assumes root access was obtained via sudo in the time out (grace) time ?

The author of that post obvioiuly does not udnerstand sudo.

Try it yourself, on a virtual machine if you like.

Open a terminal, run a command with sudo, enter your password. Now ssh into the server. Try running a command with sudo, what happens ? What happens is that you are again asked for a password.

There are many many ways an intruder can obtain root acces if they have shell access to an account that has root access.

Note: The ssh key was stolen, not cracked, and we have no idea how root access was then obtained.

From that I would conclude: secure your ssh key and use passwords (it must have either been a passwordless key or the cracker knew the password).

But the author of the article makes some good points, but makes sweeping (and IMO) unfortuinate conclusions and in general may of the claims and conclusions are simply untrue.

If you do not have the experience to know the good from the bad advice in that article, I would not then advise you accept it at face value.

Just as with my example of sudo, the author is misinformed about several things and as a result, at a minimum, "throws out the baby with the bath water".

---

### Post by flyingsliverfin on 2011-03-27
here's the ssh -vvv:

```
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/joshua/.ssh/identity
debug3: no such identity: /home/joshua/.ssh/identity
debug1: Trying private key: /home/joshua/.ssh/id_rsa
debug3: no such identity: /home/joshua/.ssh/id_rsa
debug1: Trying private key: /home/joshua/.ssh/id_dsa
debug3: no such identity: /home/joshua/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
ssh@localhost's password: 
debug3: packet_send2: adding 48 (len 67 padlen 13 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug3: Wrote 144 bytes for a total of 1271
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug3: Wrote 128 bytes for a total of 1399
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PATH
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env SPEECHD_PORT
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env XAUTHORITY
debug3: Ignored env COLORTERM
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: Wrote 448 bytes for a total of 1847
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Linux joshua-desktop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

*** System restart required ***
Last login: Sun Mar 27 16:42:17 2011 from localhost
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 6 c -1
debug3: Wrote 32 bytes for a total of 1879
debug3: Wrote 64 bytes for a total of 1943
Connection to localhost closed.
Transferred: sent 1744, received 2568 bytes, in 0.2 seconds
Bytes per second: sent 7011.5, received 10324.3
debug1: Exit status 1

```

oops hadn't realized i needed to restart :) installed updates

---

### Post by CharlesA on 2011-03-27
I know I've seen it before, but I can't recall which thread it was in.

---

### Post by msandoy on 2011-03-28
Regarding your ssh login problems with being dropped just after entering password, there is some info on this link:
[http://www.linuxquestions.org/questions/linux-general-1/connection-to-ssh-closing-immediately-520565/](http://www.linuxquestions.org/questions/linux-general-1/connection-to-ssh-closing-immediately-520565/)
Not the exact same problem, but reinstalling ssh worked in that case.

There is also the remote posibility that you have disabled your account.
[http://ubuntuforums.org/showthread.php?t=1455104](http://ubuntuforums.org/showthread.php?t=1455104)

I can't find anything else similar to your problem, even tough there is something lingering in the back of my head. The scenario seems oddly familiar somehow.

---

### Post by bodhi.zazen on 2011-03-28
> **msandoy said:**
> I have to say, I'm a bit surprised about the attitude of the forum staff here regarding changing the ssh default port. I have a server myself, on a budget line, it has been running on a 2 Mbit SHDSL line for a few years. And while I was using default port 22, I had frequent connection problems to the internet with the other computers on my network. I can tell you that when your server is being attacked with 1500+ login requests per hour, your internet is going to suck big time. Change away from the default port. It might not do much for security, but it will make your internet life easier.
Denyhosts and random ports are a blessing.

I also think you misunderstand what the staff, myself included are saying.

Typically the advice to change the port comes up in the discussion of security and changing the port does very little to increase security.

Yes it will quiet the logs and most of the scripts target port 22, but if you use keys and disable passwords your are more secure then changing the port alone.

Another point, 1500 connection attempts and hour is actually fairly trivial and should not result in a dos.

One attempt / sec = 60 sec x 60 min = 3600 attempts / hour and even that rate should be rather trivial for most any server.

If you wish, you can limit ssh connections via iptables.

You very well may have had some kind of a dos , and  changing the port may have improved your performance, and that is a valid reason to change the port, but understand that experience is not "typical" and is not what I would expect to apply to most people.

I have run many ssh server on port 22 for many years and have never seen a dos on port 22 the way you describe from these "script kiddies".

---

### Post by BkkBonanza on 2011-03-28
In your ssh -vvv dump. After login it says "recd eof". I take this to mean ti thinks the channel from your end has sent eof. I suspect some setting that is disallowing you and forcing a disconnect. Are you sure that you haven't set the server to ForceCommand mode? Or perhaps some other unusual setting. ssh with -c but no command given?

What is the full command you are using when you connect?  ssh...etc.

---

### Post by msandoy on 2011-03-28
> **bodhi.zazen said:**
> I also think you misunderstand what the staff, myself included are saying.

Typically the advice to change the port comes up in the discussion of security and changing the port does very little to increase security.

Yes it will quiet the logs and most of the scripts target port 22, but if you use keys and disable passwords your are more secure then changing the port alone.

Another point, 1500 connection attempts and hour is actually fairly trivial and should not result in a dos.

One attempt / sec = 60 sec x 60 min = 3600 attempts / hour and even that rate should be rather trivial for most any server.

If you wish, you can limit ssh connections via iptables.

You very well may have had some kind of a dos , and  changing the port may have improved your performance, and that is a valid reason to change the port, but understand that experience is not "typical" and is not what I would expect to apply to most people.

I have run many ssh server on port 22 for many years and have never seen a dos on port 22 the way you describe from these "script kiddies".

As I said near the bottom of my post, it might not do much for security. After changing the port, I have had a lag free internet. My server has never been compromised, but it has been the target of a few brute force attacks. Those I keep in mind as learning experiences. Currently I'm reading up on O'Reilly's SSH The secure Shell, The definitive Guide. Have to take it slow, since I'm away from my server for months at a time, and if I mess it up, I do not have anyone in the vincinity to fix my mistakes.

I did do a geographical lookup of those attacks, I have always heard that most attacks originate out of china, but actually USA and eastern europe took that prize. Not an accurate way of determining the origin, since most likely the attacks were run from hijacked servers. It just gave me an eyeopener.

I also use lots of different computers to log in with, so keys are not ideal. In a previous post, I suggested password cards. At least they give a password you can't find in a dictionary.

---

### Post by flyingsliverfin on 2011-03-28
@BkkBonanza

I'm using ssh -p port IP to connect. 

where would I find the ForceCommand option? I can't find it in the sshd_config file.

The only things I've changed in the sshd_config file are port number, to use a banner, disallow root login, and only allow the user "ssh" to login (by using Denyuser j r combined with AllowUser ssh)

---

### Post by cariboo on 2011-03-28
Check [man ssh]("http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh+1") for info on force-commands-only. This only works for ssh, if you are using openssh-server, the commands don't work.

---

### Post by BkkBonanza on 2011-03-28
ForceCommand is described in **man sshd_config**. If it's not present in yours then it's not active. It was just something to check as I couldn't think of why else a connection would be dropped after already making it thru authentication.

Try removing your deny/allow rules to make sure they aren't interfering.

What does your /var/log/messages or /var/log/auth.log say relative to the login event that shows up?

---

### Post by d3v1150m471c on 2011-03-28
you should also consider setting an acceptable range list for ip's that can access your system. IE
192.168.1.0/24 or 192.168.0.0/16, of course it won't be lan ip's you're setting it up for but it tightens up security quite a bit by limiting who could even potentially try and exploit ssh.

---

### Post by msandoy on 2011-03-28
> **flyingsliverfin said:**
> @BkkBonanza

I'm using ssh -p port IP to connect. 

where would I find the ForceCommand option? I can't find it in the sshd_config file.

The only things I've changed in the sshd_config file are port number, to use a banner, disallow root login, and only allow the user "ssh" to login (by using Denyuser j r combined with AllowUser ssh)

You say you use "ssh -p port IP" and that you have only allow the user ssh to login. This will try to log you in with your username, and you will be kicked if it is not "ssh".
In that case, User ssh needs a home and a shell, if I'm not mistaken, and you need to use "ssh -p port ssh@IP" to login.

Just a tought.

---

### Post by flyingsliverfin on 2011-03-29
Strange, I just reinstalled the openssh-server package (sudo apt-get purge openssh-server and then sudo apt-get install openssh-server), but it still drops the connection right away.

---

### Post by bodhi.zazen on 2011-03-29
I have not seen that message before.

One general comment - You seem to be using a password to log into the server and I highly suggest you use keys.

I found two threads describing a similar error message :

[http://ubuntuforums.org/showthread.php?t=1511773](http://ubuntuforums.org/showthread.php?t=1511773)

[http://ubuntuforums.org/showthread.php?p=9959476](http://ubuntuforums.org/showthread.php?p=9959476)

There is also this discussion:

[http://serverfault.com/questions/92932/how-does-ubuntu-keep-track-of-the-system-restart-required-flag-in-motd](http://serverfault.com/questions/92932/how-does-ubuntu-keep-track-of-the-system-restart-required-flag-in-motd)

So one question, did you upgrade packages on the server recently and have you rebooted ?

---

### Post by flyingsliverfin on 2011-03-29
I just realized that because ssh's account has an ID < 1000 it's shell is set to /bin/false ](*,) that  means their ssh shell would immediately close right?

So is there a way to let them have an extremely unpriviliged shell that can't use sudo?

---

### Post by flyingsliverfin on 2011-03-29
Well now its working! here's what I did: changed the shell in /etc/passwd to /bin/bash. Apparently since I created the user using adduser --system it's in the nogroup group and not in the sudoers file, so the user doesnt have permission to use sudo, which is what I wanted.

Now to learn about Iptables and how to stop the person that ssh's in from using 'cd ..' beyond their home directory

Thanks!

---

### Post by bodhi.zazen on 2011-03-29
> **flyingsliverfin said:**
> I just realized that because ssh's account has an ID < 1000 it's shell is set to /bin/false ](*,) that  means their ssh shell would immediately close right?

Yep, that would be the problem.

> So is there a way to let them have an extremely unpriviliged shell that can't use sudo?

Make an account that is not in the admin group.

If you need more then that, use apparmor.

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

alternate would be to use a chroot / LXC

---

### Post by CharlesA on 2011-03-29
Ah hah. That explains it then.

Glad you got it working. :)

As for preventing someone sshed in from accessing the while file system, look into chrooting them. See here for an example: [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by flyingsliverfin on 2011-03-29
spring break projects: chroot, iptables :) Not now though... lots of hw coming up :(

---

### Post by msandoy on 2011-03-29
Glad it worked out at last. :-)

---

### Post by flyingsliverfin on 2011-03-29
AAAHHHHHHHHHH new error:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
c3:2b:59:47:cd:1b:09:db:7c:ae:a9:bd:e0:7f:d6:7c.
Please contact your system administrator.
Add correct host key in /home/joshua/.ssh/known_hosts to get rid of this message.
Offending key in /home/joshua/.ssh/known_hosts:4
RSA host key for [localhost]:49182 has changed and you have requested strict checking.

```

??? I was only connecting to localhost...

---

### Post by bodhi.zazen on 2011-03-29
Most likely this is either a fresh installation or the ip address of the server has changed (dhcp rather then a static IP address).

I have a brief note about this message here :

[http://bodhizazen.net/Tutorials/SSH_overview#Security](http://bodhizazen.net/Tutorials/SSH_overview#Security)

Otherwise google search ssh host keys.

---

