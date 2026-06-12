---
title: "Just remenbering Firehol (no pub)"
date: 2007-08-03
forum: Server Platforms
---

### Post by ruibernardo on 2007-08-03
I'm no iptables expert, I just like simple things (like Ubuntu). I've used iptables before, but it's too complicated for simple jobs, and althought it is complete, it's a pain in the *** to set it up for new Linux/ubuntu users. And as Ubuntu comes with no firewall enabled, it's too sad that, for Home/Desktop users, the firewall Ubuntu officially supports is Shorewall, since Shorewall is "almost as complicated" as Iptables. 

I think that Shorewall must be good for really heavy stuff (many servers, many networks, many routers), but for the general Desktop/Home users with a home lan, it is too heavy, and Firehol does all Shorewall does, but with less, and with less complicated, setup.

I'm just remembering Firehol, a great firewall for those who are tired of using Firestarter, and are confronted with it's stiffness to tweaking (bad for wireless and other stuff), and for all the others who like a personal firewall, but don't like to loose time with iptables syntax.

It isn't a firewall for those who like to spend time watching "live" connections (no GUI as Firestarter has), but if you spend some time (like 1 hour or 2, who knows, maybe a bit more) configuring it, you will get a firewall that uses almost(?) all iptables capabitilies, without too much pain, and just with a dozen lines in the config file.

Check it's tutorial and it's services «ready to use» on it's [webpage]("http://firehol.sourceforge.net/")!

Things like squid/Dansguardian and Moblok, or just opening ports to smb or ssh on the home lan interface is just too easy.

To bad that Firehol package isn't being maintained lately by Debian/Ubuntu package maintainers.

---

### Post by ruibernardo on 2007-08-04
**To install Firehol**:

```
sudo apt-get install firehol
```Due to a little bug, the Debian/Ubuntu version of Firehol doesn't work out of the box in Feisty. To make it work, do the following in a terminal (thanks Austin) ([https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/23](https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/23)):

```
sudo -i
sed 's/%q/%b/g' /lib/firehol/firehol > TMPFILE && mv TMPFILE /lib/firehol/firehol
chmod 744 /lib/firehol/firehol

```After that, you can activate it to work on boot. Edit the file /etc/default/firehol:

```
sudo nano /etc/default/firehol
```And change the line "START_FIREHOL=NO" to "YES":

```
START_FIREHOL=YES
```If you have an interface that takes a little time to become active (modem, wireless, whatever), add it on the line "WAIT_FOR_IFACE=".

Restart firehol with:

```
sudo firehol restart
# write "commit" if no errors as occurred.

```If you are using SSH, watch out not to be locked outside the box (see example 2).

**Example 1** - A computer connected to the internet with no servers:

It's very easy. Install firehol and make it active in the "/etc/default/firehol" file, restart it, and you will have a stealth computer on the net.

**Example 2** - A computer connected to the net with SSH server (or FTP, or HTTP or else):

It's easy. Install Firehol, make it active in the "/etc/default/firehol" file, edit its configuration file with 

```
sudo /etc/firehol/firehol.conf
```Add "**server ssh accept**" between "interface any world" and "client all accept". Replace "ssh" with "ftp" or "http". More services are available. Look for them on [Firehol webpage]("http://firehol.sourceforge.net/") (Services).

Restart firehol ("sudo firehol try"). 

**Example 3** - A computer connected to the internet with Squid/dansguardian:

Install Squid:

```
sudo apt-get install squid
# it will end with an error, don't bother, just do the following.
```Edit Squid configuration file:

```
sudo nano /etc/squid/squid.conf
```And set the "visible_hostname" variable. Search for it in the file, and after its comments add:

```
visible_hostname www.server.net
# "www.server.net" is an example.
```Search for the line "http_port 3128" and add "transparent" to it.

```
http_port 3128 transparent
```
Search for the line "cache_efective_user", uncomment it so it looks like:

```
cache_effective_user proxy
```Restart Squid with:

```
sudo /etc/init.d/squid restart
```Now install Dansguardian:

```
sudo apt-get install dansguardian
```If the installation fails with errors, don't bother. Complete it with:

```
sudo apt-get install -f
```Edit it's configuration file:

```
sudo nano /etc/dansguardian/dansguardian.conf
```And delete or comment the following line with a cardinal ("#") so it looks like this:

```
#UNCONFIGURED - Please remove this line after configuration
```Restart Dansguardian with:

```
sudo /etc/init.d/dansguardian restart
# wait a moment while it restarts. Don't bother about Clamav message.
```Now edit Firehol configuration file:

```
sudo nano /etc/firehol/firehol.conf
```And add the following lines right after "version 5" line:

```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "proxy proxy"
```Restart Firehol with:

```
sudo firehol try
```Try it on a browser you have installed.

---

### Post by ruibernardo on 2007-08-04
Well, the Squid/Dansguardian part was bigger than the rest...

Now, I don't have a home lan (just vmware-server), so if somebody has one and uses Firehol, post here how to make it work. There is a little tutorial on the [website]("http://firehol.sourceforge.net/") (Tutorial), but surely someone as a simple explanation to run Firehol with a network. Any volunteer? :)

---

