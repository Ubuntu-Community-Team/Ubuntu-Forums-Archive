---
title: "SSH-ing into localhost -or- The Password of Mystery"
date: 2016-02-29
forum: Server Platforms
---

### Post by spacer.x-infinity on 2016-02-29
Hi,
I'm trying to pipe my Squid3 proxy server traffic through an SSH tunnel using this command:

```
ssh -f localhost@public-hostname-of-proxy-server -L 3128:private-ip-of-proxy-server.com:3128 -N
```

However, as soon as I run it, I am prompted for a password which, apparently, is not the same as my primary user password that I use everyday to log in to my desktop. I've tried it repeatedly without any typos and just get back a *Permission denied, please try again* message. I also tried my wifi password as well as 'admin,' 'root,' and 'password,' none of which worked. I read somewhere online that the root password and localhost password are the same but that, by default, this password is unknown to the user and must be reset using the *sudo passwd root* command. I tried doing this but still get the same result. Can someone tell me how to get around this, whether it is by resetting the localhost password by some other means, finding out what it is, or bypassing it altogether? Thanks for any help.

---

### Post by spjackson on 2016-03-01
You are trying to connect as user localhost to server public-hostname-of-proxy-server because that's what localhost@public-hostname-of-proxy-server means. Is there really a user account called localhost on public-hostname-of-proxy-server? This would be somewhat unusual, but there's nothing to stop you creating a user called localhost if you wanted to.

localhost is normally used to mean *this computer,* e.g.
```

$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.083 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.091 ms

```

---

### Post by Bucky Ball on 2016-03-01
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2016-03-01
I'd use OpenVPN to set up a simple [static, shared-key tunnel](http://openvpn.net/static.html) between the machines myself.  That's a lot more flexible that SSH port forwarding.

---

### Post by spacer.x-infinity on 2016-03-01
Hmmm... I don't think I'm following you. I was under the impression the that "localhost@public-hostname-of-proxy-server" was itself the hostname of the proxy server. To clear, I'm using "localhost@primary-user-Satellite-L500" because "primary-user" is the name of my main user account on Kubuntu 14.04 and "Satellite-L500" is the type of laptop I'm using. "Hostname-of-proxy-server" is just a place-holder used in [this tutorial](http://evanhoffman.com/2010/09/17/using-ssh-tunnel-squid-to-create-a-private-encrypted-proxy-for-true-private-browsing-mostly/) to denote whatever username the particular user happens to be using. In any case, this is a minor point. 

What I think I'm really caught up on here is the idea that "localhost" is distinct from "@primary-user-Satellite-L500" in the phrase "localhost@primary-user-Satellite-L500." If this isn't the hostname of my proxy server and neither is "localhost" standing alone, then what is? The way the above tutorial explained it to me was like this:

> 
[h=2]Step 3:Create the SSH tunnel[/h] I run Linux, so that&#8217;s the syntax I can provide (You can use putty to do this from a Windows machine):

```
ssh -f evan@public-hostname-of-proxy-server -L 3128:private-ip-of-proxy-server.com:3128 -N
```

This opens an SSH connection from your local machine (port 3128) to the  remote server&#8217;s private IP on port 3128 (3128 being the default port on  which squid listens).  So connections to localhost:3128 will be  forwarded over the SSH tunnel to port 3128 on the other machine&#8217;s  private IP.



My understanding was that localhost (whatever its true username might be) connects to the squid3 proxy server via port 3128; and that the above command merely directs SSH to create a tunnel to this port via the localhost IP (127.0.0.1). I'm obviously quite mixed up here and don't understand the difference between the localhost username and the proxy server hostname. And I'm still not clear why I'm being prompted for a password that I don't have when I run the above command. 

Thanks in advance for any additional help.

---

### Post by spacer.x-infinity on 2016-03-01
> **SeijiSensei said:**
> I'd use OpenVPN to set up a simple [static, shared-key tunnel]("http://openvpn.net/static.html") between the machines myself.  That's a lot more flexible that SSH port forwarding.

I actually tried that already but then opted for SSH port forwarding because the setup process for OpenVPN got to be too confusing. Because of improper iptables and IP routing rules, my SSH connection was essentially blocked. I added a bunch of new rules to iptables in an effort to make SSH traffic bypass the VPN but this didn't seem to make a difference. Although I found a couple tutorials that tried to explain how to modify your routing rules to make this happen, I didn't feel confident enough with IP routing to follow though with it. In stead, I just decided to purge *openvpn easy-rsa* from my system and try something a little less complicated. My main interest here is just to find a stable method of browsing the web anonymously without sacrificing functionality. I have the Tor browser installed but it's really picky about the sorts of cookies it will accept and there are some websites that I still want to be able to log into. I'm not too concerned about the security of my SSH connection to my other machine because I already have public key authentication working.

---

### Post by SeijiSensei on 2016-03-01
"Localhost" is the name given to the 127.0.0.1 address that exists on pretty much every machine.  It's a virtual network interface that you can only connect to from the local machine.  It's not a username.  If you want to connect to another machine with SSH, you need to use
```
username@remote_host
```
For instance, if the remote server had a user called "barbara", you could log into her account with 
```
ssh barbara@remote_server_name
```
You'll be prompted for Barbara's password unless you use keys.

> **spacer.x-infinity said:**
> Instead, I just decided to purge *openvpn easy-rsa* from my system and try something a little less complicated.

Did you read the link I posted?  [http://openvpn.net/static.html](http://openvpn.net/static.html)

It's hard to imagine something easier than that.  Also OpenVPN uses SSL and goes through most firewalls without any extra configuration on the client end.  On the remote server you'd need to open port 1194 unless you choose, as I do, to use custom high ports like 54321.  Then you would need to open that.

---

### Post by spacer.x-infinity on 2016-03-01
Thanks for the suggestion, SeijiSensei. I'll certainly give that link a closer look. On closer inspection, it does look a little less complicated than whatever I was trying to do.

---

### Post by spacer.x-infinity on 2016-03-01
Alright, I started to follow along with that tutorial on OpenVPN static-key tunnelling and all was going fine until it came time to transfer the key over to the remote machine (a Kubuntu 14.04 VirtualBox VM on a Windows 7 host, if that's relevant). The OpenVPN package installed fine, generating the key and moving it into the /etc/openvpn directory wasn't a problem, and neither was creating the *server.conf* file. However, when I run *sudo scp static.key 192.168.0.108:/etc/openvpn*, I get prompted for* root@192.168.0.108's password*. When I enter the primary-user password to the VM, I run into basically the same problem that I did with when trying to tunnel into *localhost@primary-user-Satellite-L500* with the SSH port forwarding approach: *Permission denied, please try again.* I even tried resetting the root password on the VM with *sudo passwd root* but this didn't change anything. What am I doing wrong?

---

### Post by SeijiSensei on 2016-03-01
If you gave root a password on the remote, use 
```
sudo scp static.key root@192.168.0.108:/etc/openvpn
```
Otherwise it will look for a user on the remote with the same name as the user on the client.

If that doesn't work, can you connect as a user with sudo permissions on the remote?  Log in as that user and use scp from there.  Alternatively just copy the key with copy and paste.  It's just a plain-text file.  Open the file with the key on the client, copy the contents to the clipboard, then log into the remote, create an empty file with "sudo nano keyfile_name" and paste.

---

### Post by spacer.x-infinity on 2016-03-01
For some reason, SSH is blocked again. Tried the first command you suggested and here's what I got:

```

ssh: connect to host 192.168.0.108 port 22: No route to host
lost connection

```

Also tried logging into the VM so that I could SSH into the server from the client side but noticed that my bridged connection has somehow vanished from my list of available networks. When I hold my cursor over the icon, a message just pops up that says "NetworkManager not running." This didn't happen until after I reinstalled OpenVPN. I'm sorry to put you through your paces here but I'm honestly at a loss about what to do next.

---

### Post by spacer.x-infinity on 2016-03-01
After reading up on this a little further, I have a sneaking suspicion that my current problem has something to do an improperly configured firewall. Tweaking my iptables rules to see if this makes a difference...



Update:

Added the following rules to iptables on both the server and client machines:

```

sudo iptables -A INPUT -p udp --dport 1194 -j ACCEPT
sudo iptables -A INPUT -i tun0 -j ACCEPT

```

Nothing has changed as a result. SSH connection attempts from both sides are still saying "No route to host" and the bridged connection in the VM is still missing from the list of available connections. Not really sure what to do next but any further help would be appreciated.

---

### Post by SeijiSensei on 2016-03-02
I'd take down the firewalls until you get this sorted out, or strip them down so that both ends accept all traffic from the other host/subnet and block everything else.

---

### Post by spacer.x-infinity on 2016-03-02
I did as you suggested and stripped down the firewall to include only these rules for the input chain on both server and client machines:

```

sudo iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT 
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -j DROP

```

As a result, my SSH connection has been restored. However, I am only able to access the directory containing the *static.key* from the client side because trying to *scp* it over from the server side results in a prompt for the root password of the remote machine. Is there a way to copy-and-paste the *static.key* from the /etc/openvpn directory on the server machine to the one on the client machine without using the *scp* command and without resulting in a prompt for the client's root password? I assume it would involve the *cp* command but I don't know the exact syntax. Thanks again for your help.

---

### Post by spacer.x-infinity on 2016-03-02
Never mind. Figured it out on my own. Used this command:

```
cat static.key | ssh 192.168.0.108 "cat > remote"
```

This placed the static key in the home directory of my client machine with the assumed file name of "remote." Then all I did was:

```
mv remote static.key
```

to rename the file, followed by:

```
mv static.key /etc/openvpn
```
 
to place it in my client machine's *openvpn* directory. 

Now to proceed with the remainder of the tutorial. Hopefully it will come together without any more substantial glitches...

---

