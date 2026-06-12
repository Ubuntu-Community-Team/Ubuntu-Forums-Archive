---
title: "SSH repeatedly locked out by denyhosts after UFW install"
date: 2012-04-14
forum: Security
---

### Post by slowtrain on 2012-04-14
Hello! I experimented with going to UFW, after reading the sticky in Security Discussions.  After turning it on w/ GUFW, *and even after allowing SSH access using the preprogrammed GUFW rule to allow port 22 from anywhere*, I can sign on once from SSH before being permanently locked out.

The basic problem looks like this: Reboot the machine. Completely remove and then reinstall denyhosts. Remove my laptop's address from /etc/hosts.deny on my desktop. Connect from the laptop to the desktop using ssh (providing my password just once and getting in without problems). And, without doing anything else, look back in my hosts.deny file and my laptop's ipaddress has reappeared in it!  Sign out, try to connect again, and I either get an ssh timeout or "ssh_exchange_identification: Connection closed by remote host."

The main purpose of this desktop is to run analyses remotely, so this problem is rendering my machine unusable.

My best guess is that ssh is shifting from port 22 to some other port once the connection is formed and denyhosts then treats the connection as illegitimate and adds the ipaddress to hosts.deny. For example, the auth.log entry for my ssh connection looks like this: Accepted password for slowtrain from myLaptopIPaddress port 55379 ssh2 . I'm just using standard ssh syntax and the firewall won't accept anything coming in other than on port 22, so I can only imagine ssh is moving the connection to this other port. It probably does this normally to allow multiple ssh connections.

Before putting UFW on my machine I didn't have this problem and could connect w/ SSH as much as I liked. On the other hand, I don't know for certain that UFW caused the problem. I've now shut down UFW and reinstalled Firestarter, but the problem persists. On the other hand, maybe something UFW did to some configuration file that remains is making this happen? Thoughts?

---

### Post by darkod on 2012-04-14
Since ufw and gufw are only a front end for iptables, what you could try is:
sudo iptables -F

That will flush all rules that might be left over from ufw. Also, disable ufw before that.

I guess the server is at home so you can access it directly, otherwise be very careful with the firewall rules if you only have remote access. For example, the -F will also flush the rule allowing your connection to the server. I have locked myself out of a remote server like that. :)

I am not familiar with denyhosts. Wouldn't you rather use only a firewall with which you can also limit hosts? Maybe the combination denyhosts + ufw is working weird.

---

### Post by CharlesA on 2012-04-14
Did you whitelist the IP you are connecting from?

Connecting from a random high numbered port is fine - the destination port is always going to be 22 (unless you change that in the sshd config)

Does the same thing happen if you flush all the firewall rules?

---

### Post by slowtrain on 2012-04-14
Hi folks:  The desktop is at my workplace, and I'm currently at home.  I can't access it remotely because of this problem.  

When I'm next at the office (likely soon), I'll try flushing the iptables rules--thanks for the tip!  I had thought, though, that iptables doesn't store its rules (I haven't been able to find where) so rebooting would have had the same effect.  Apparently not.

My ipaddress from home isn't static (I have standard Comcast service).  I also only get to see a private address for my own computer, so can't easily track what ipaddress my desktop sees.  Am guessing it's usually the same, but maybe not always.  If I set up my firewall to only accept from a particular ipaddress, I'd be potentially locking myself out some of the time.  Also, the machine seems to be the target of a lot of attempts to guess passwords, which is why I have denyhosts on it.  

Maybe a solution is port knocking plus a firewall that only accepts from the ipaddress range of my Comcast service--though I don't know what that is.  Guess I should call.

Thanks again!

---

### Post by darkod on 2012-04-14
You can view the iptables rules with:
sudo iptables -L -n -v

If you have set up any nat/port forwarding rules, you can see those in the *nat table:
sudo iptables -t nat -L -n -v

Flushing is:
sudo iptables -F
sudo iptables -t nat -F

On a recent firewall project I also used ufw (without gufw), but later I actually found out that using iptables is not as complicated as it sounds, with the help of this forum.

Here is my thread, there is a number of interesting advices especially from page 3 onwards:
[http://ubuntuforums.org/showthread.php?t=1947308](http://ubuntuforums.org/showthread.php?t=1947308)

The beginning of the thread is for a different problem that I managed to solve, and the discussion continued how easy/difficult is it to use iptables.

The approach to have iptables.rules file that includes your rules and gets loaded at boot is very good. Wish I knew that 3 weeks ago.

You can basically lock down as much as you want with iptables/ufw. Depending what type of attacks the machine receives, and what services does it need to have available to the public.

Having a dynamic public IP at home doesn't help limiting access. I don't know if some dynamic dns solution might help.

---

### Post by slowtrain on 2012-04-16
Hi folks:  Thanks for all the input!  Nothing seemed to work, but I finally figured out that the sole problem was denyhosts itself, not something w/ the firewall.

I would, for example, disconnect my machine from the internet, erase the ipaddress of my laptop from hosts.deny--presumably the list of hosts that are barred from access by denyhosts-- wait a minute or two, and the ipaddress was back in hosts.deny, like some kind of evil magic trick.  Seems that there are 5 files in which denyhosts stores information about ipaddresses, 4 in /var/log/denyhosts and then /etc/hosts.deny.  W/o my entry erased from all 5 files AND erasing any reference to my laptop's ipaddress in auth.log, the ipaddress would reappear in hosts.deny.  It seems that denyhosts scans auth.log, so that can make the ipaddress reappear as well (at least if denyhosts has lost its offset in the log).  I hear that denyhosts also has a sync mode which syncs 'bad' ipaddresses to some remote server.  Then it may well be neigh impossible to deban yourself from your computer.  denyhosts could certainly use much clearer documentation.  

Thanks for your time!  Your comments helped me rule out possibilities as to what might be causing the problem.  I guess I was too hung up about the coincidence that I happened to be experimenting with UFW at the same time.

---

### Post by vdobriakov on 2012-10-28
Thanks slowtrain!

* stopping the denyhosts service `sudo /etc/init.d/denyhosts stop`
* purging /etc/hosts.deny and /var/log/auth.log
* starting denyhosts `sudo /etc/init.d/denyhosts start`

helped!

---

