---
title: "Secure web browsing from insecure wi-fi hotspots?"
date: 2012-05-25
forum: Server Platforms
---

### Post by martago on 2012-05-25
What is the best and simplest solution for secure web browsing (like  home banking) from an insecure connection, like a wi-fi hotspot?
There are many solutions based on third-party proxy servers, like Bit Box ([www.sirrix.com]("http://www.sirrix.com")).   But a secure connection that is dependent of a third-party server may  not be a real secure solution because you are relying on the honesty of a  third-party company that will not take advantage of the information you  are trusting them to encrypt and circulate in the net.
Open VPN allows the secure communication between an insecure computer  and a server, but it only allows access to shared folders and printers.   To have then access through that server to the web you will need a  proxy server, a real proxy server and not a proxy that only caches web  pages for the sake of speed.
Does anyone knows what is the most adequate linux solution for this scenario?  Thank you for your help.

---

### Post by haqking on 2012-05-25
> **martago said:**
> What is the best and simplest solution for secure web browsing (like  home banking) from an insecure connection, like a wi-fi hotspot?
There are many solutions based on third-party proxy servers, like Bit Box ([www.sirrix.com]("http://www.sirrix.com")).   But a secure connection that is dependent of a third-party server may  not be a real secure solution because you are relying on the honesty of a  third-party company that will not take advantage of the information you  are trusting them to encrypt and circulate in the net.
Open VPN allows the secure communication between an insecure computer  and a server, but it only allows access to shared folders and printers.   To have then access through that server to the web you will need a  proxy server, a real proxy server and not a proxy that only caches web  pages for the sake of speed.
Does anyone knows what is the most adequate linux solution for this scenario?  Thank you for your help.

None, dont conduct banking transactions on public (insecure) networks, the end ! ;-)

---

### Post by LHammonds on 2012-05-25
> **haqking said:**
> none, dont conduct banking transactions on public (insecure) networks, the end ! ;-)
qft

---

### Post by eleftg on 2012-05-25
I don't understand what exactly is your problem. You always need to trust at least one link of a security chain. Even if you rent a VPS box, then setup openvpn from scratch, you need to trust that the VPS provider won't copy your certificates from your box.

> Open VPN allows the secure communication between an insecure computer and a server, but it only allows access to shared folders and printers. To have then access through that server to the web you will need a proxy server, a real proxy server and not a proxy that only caches web pages for the sake of speed

The above is not correct. Why just shared folders and printers? You can surf the web through an OpenVPN tunnel and you can also surf the web through an SSH SOCKS proxy always having the IP address of the server. The tunneled link between you and the server is secure. However, the route between the server and the web is unencrypted.

For example if you just want to access your home banking service (even in an unsecure wifi network) the only thing that you need to check is having SSL encrypted traffic between you and your bank ([https://)](https://)). Because in case it's not SSL encrypted, then even if you are behind a vpn or SSH SOCKS proxy, your traffic goes encrypted between you and the server, but from the server to the outter space it's unencrypted. So any compromised point in that route can cause big trouble.

---

### Post by TheFu on 2012-05-25
[B]Some call me paranoid - how much is not having your accounts hacked worth?

[/B]It is critical that the DNS being used is 100% trusted, not just that SSL is being used and manually validated as "reasonable" for every cert. I'm not smart enough to know all the real cert-authorities from the fake ones.  Could you tell a spoofed Verisign cert from the real one when the DNS was hacked too?  Using OpenVPN and proxying all the traffic from a trusted server + network is a stop-gap solution and should only be used in emergencies, not as a default.

SSL can be checked at runtime and those checks can be helped by browser extensions, but then you add more complexity and the possibility that someone has touched something in the middle (PC, software, network, certificate, DNS), it adds risk.

For things like online banking, I'd use a different machine than your "daily driver" to further reduce risks.  If this is for home use, then your liability is pretty limited, however, a business account(s) is involved, then the normal account liability protections do not apply.  That means if there is a breach that clears your entire business account, you can lose the total amount of money in the account. 

There are lots and lots of small businesses who have lost hundreds of thousands of dollars by using a compromised PC for banking. Using Linux helps, but it is not fool proof and does not make anyone 100% uncrackable.

I don't want the hassles and don't want my business accounts hacked, so it is just easier to have a PC setup with a Live-CD linux distro - (like TinyCORE) at home that I use to access only banking websites and no other purpose. That PC is an old, cheap, Pentium4. It doesn't have a HDD installed, just a NIC and DVD drive to boot off.

A case could be made to use a virtual machine instead of the physical PC, but if the hostOS is penetrated, then you could be just as screwed.

I would never (ok, 99.99999%) use an untrusted network to access banking. Not a hotel, not a coffee shop, and definitely not a free wifi at any restaurant or bookstore.  **At a college, I'd rather NOT get on the network at all.**  Banking can wait until I'm back home. This is workable for me.

---

### Post by eleftg on 2012-05-25
I pretty much agree with 100% of what TheFu says. But i will just give an example of why normal users are disgusted by this security paranoia:

In my workplace, our everyday work involves frequent ssh sessions to multiple servers (hardened as much as one could possibly harden them). We all use almost every flavour of Linux and strong certificates to log in. Still, you can't imagine how many - countless - times I needed to gave lectures on "man-in-the-middle" attacks until every colleague adopted the practice of cross checking the host key fingerprint when logging in for the first time (and not just typing "yes"). Everybody told me: "Come on now... It's SSH...  how in the world can anybody break in!"

It goes the same with 70% of computer users having their date of birth as a password for everything.

[Sigh] In an ideal world your above post would constitute a chapter in a short standalone course about "Computer security in every-day life" in high-school. But then, if somebody illiterate in computers security has to mind all this in order to use online banking, why not stand in line in front of the bank teller? :-D

---

### Post by anonymouschief on 2012-05-25
> **martago said:**
> What is the best and simplest solution for secure web browsing (like  home banking) from an insecure connection, like a wi-fi hotspot?


This could either be a Server-related, or Desktop-related question. The OP's question does not specify. Please specify if your question is based on #1 or #2 below. Please move the thread to the Desktop forums if the question relates to #2.
[LIST=1]
[*]Is the OP looking towards hosting a server that will provide this "secure" connection between nodes, as a service?
[*]Does the OP need help finding a service that will secure their browsing experiences?
[/LIST]

---

### Post by Enigmapond on 2012-05-25
> **anonymouschief said:**
> This could either be a Server-related, or Desktop-related question. The OP's question does not specify. Please specify if your question is based on #1 or #2 below. Please move the thread to the Desktop forums if the question relates to #2.
[LIST=1]
[*]Is the OP looking towards hosting a server that will provide this "secure" connection between nodes, as a service?
[*]Does the OP need help finding a service that will secure their browsing experiences?
[/LIST]

There is no foolproof way of securing a connection on a public network. Don't do banking or other sensitive transactions on one. To do so you are doing at your own risk. You cannot be secure on an insecure network....

---

### Post by kennethconn on 2012-05-25
Have to chime in like everyone else here - I never do anything like that on a public wi-fi hotspot, simply use these for catching up on the latest news and forum posts.

---

### Post by Irregular Joe on 2012-05-25
If you are accessing public wifi from your laptop, and have a machine at home (or a VPS system you reasonably trust), you can use SSH to tunnel to the VPS and proxy out to the public Internet.

```
ssh -D 8080 vpsuser@myvps.example.com
```
This can be configured in ~/.ssh/config for even easier use:
```
Host myproxy
  HostName myvps.example.com
  User vpsuser
  DynamicForward 8080

```
Then the command would simply read:
```
ssh myproxy
```
In your browser, find the network settings, and add a SOCKS5 proxy pointing to localhost:8080

Now, when you use the browser, all of the requests will go out port 8080 to myvps.example.com before they are sent out to the Internet.  Anyone snooping on the public wifi network will not see anything but an encrypted stream.
I believe that DNS requests will go out over the proxy, as well, but someone else will need to confirm that.

Of course, I assume you have already disabled any unnecessary server processes running on your laptop before connecting to the public wifi.
Hope that helps.

---

### Post by kennethconn on 2012-05-26
I have heard about that type of setup, but never actually implemented it. It's going on the tasklist. Nice solution, Irregular Joe.

---

### Post by HermanAB on 2012-05-27
Howdy,

There are many aspects to this problem, including DNS and SSL cerificate security.  So what I do, is use a Linux laptop and tunnel to one of my own servers with SSH, then browse via that server to may bank accounts.

Because the connection is always made the same way, the system should never ask me to confirm a certificate.  If it does, then that sets off a red flag since something must have gone wrong somewhere.

---

### Post by CharlesA on 2012-05-27
> **HermanAB said:**
> Howdy,

There are many aspects to this problem, including DNS and SSL cerificate security.  So what I do, is use a Linux laptop and tunnel to one of my own servers with SSH, then browse via that server to may bank accounts.

Because the connection is always made the same way, the system should never ask me to confirm a certificate.  If it does, then that sets off a red flag since something must have gone wrong somewhere.
I have done that as well. It's easier for me to trust my own machine than it is to trust a random VPS or VPN.

---

### Post by SeijiSensei on 2012-05-27
> **Irregular Joe said:**
> If you are accessing public wifi from your laptop, and have a machine at home (or a VPS system you reasonably trust), you can use SSH to tunnel to the VPS and proxy out to the public Internet.

How cool is this??!!

I've got my laptop configured to build an OpenVPN tunnel with my house when I'm travelling, but for browsing alone Irregular Joe's solution is spectacularly easy to implement.  I have a couple of Linodes out on the Internet.  I simply ran the "ssh -D" command he suggests, then opened Firefox and told it to use SOCKS5 on 127.0.0.1 and the port I selected.  Boom, all my browsing was now going through the SSH tunnel and out the Linode.

If you want to have complete connectivity to your home, I strongly recommend using a [simple static-key OpenVPN tunnel]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  It's a bit tricky to [get the routing right]("http://ubuntuforums.org/showpost.php?p=11902967&postcount=4") though.

For simple browsing tasks, though, Irregular Joe's approach seems ideal, though it obviously doesn't solve DNS poisoning.  If someone knows of an equally easy way to set up secure UDP traffic, then you could use your home's DNS server.

---

### Post by kennethconn on 2012-05-27
Some questions I would have with Irregular Joe's solution, could your password to establish the SSH connection to home machine be snooped? Would the use of keys eliminate this?

---

### Post by CharlesA on 2012-05-27
> **SeijiSensei said:**
> 

For simple browsing tasks, though, Irregular Joe's approach seems ideal, though it obviously doesn't solve DNS poisoning.  If someone knows of an equally easy way to set up secure UDP traffic, then you could use your home's DNS server.

You should be able to pass DNS requests thru the tunnel. Firefox has a setting called: network.proxy.socks_remote_dns, which is set to false by default. Changing it to true causes dns requests to be routed thru the tunnel.

I don't know if that would necessarily prevent DNS poisoning tho.

> **kennethconn said:**
> Some questions I would have with Irregular Joe's solution, could your password to establish the SSH connection to home machine be snooped? Would the use of keys eliminate this?

An encrypted connection is established before you even enter your username. Using keys is a bit more secure than just a password, but as long as a strong password is inuse, you should be fine.

---

### Post by SeijiSensei on 2012-05-27
> **CharlesA said:**
> I don't know if that would necessarily prevent DNS poisoning tho.

I'd imagine it depends on how much trust you can place in the DNS server at the other end of the tunnel.  I use my primary server which talks directly to the roots.  That one is publicly visible, but I have another server at home, too.  It currently handles requests for a couple of local domains and forwards the rest to the public server making it, at the moment, as vulnerable as the public one.  I don't use DNSSEC yet, though I imagine the day is coming soon.  I'm not really sure how I'd know if my server's cache contained bogus A records.

> **kennethconn said:**
> Some questions I would have with Irregular Joe's solution, could your password to establish the SSH connection to home machine be snooped? Would the use of keys eliminate this?

Using keys is definitely a better option.  Not having to enter the password enables you to run a remote command via SSH non-interactively.  Charles is correct, too.  The beauty of SSH is that it encrypts all the input before sending it to the remote server making the entire conversation secure.

In Joe's example, if the user called "vpsuser" had exchanged keys with user "vpsuser" on the remote, then running "ssh myproxy" wouldn't require any confirmation.  You could then assign the command to a desktop icon or key combination that wouldn't request a password.

---

### Post by CharlesA on 2012-05-27
> **SeijiSensei said:**
> I'd imagine it depends on how much trust you can place in the DNS server at the other end of the tunnel.  I use my primary server which talks directly to the roots.  That one is publicly visible, but I have another server at home, too.  It currently handles requests for a couple of local domains and forwards the rest to the public server making it, at the moment, as vulnerable as the public one.  I don't use DNSSEC yet, though I imagine the day is coming soon.  I'm not really sure how I'd know if my server's cache contained bogus A records.



Using keys is definitely a better option.  Not having to enter the password enables you to run a remote command via SSH non-interactively.  Charles is correct, too.  The beauty of SSH is that it encrypts all the input before sending it to the remote server making the entire conversation secure.

In Joe's example, if the user called "vpsuser" had exchanged keys with user "vpsuser" on the remote, then running "ssh myproxy" wouldn't require any confirmation.  You could then assign the command to a desktop icon or key combination that wouldn't request a password.
That makes sense. If the DNS server is compromised or has it's cache poisoned, it is as good as browsing without the tunnel.

---

### Post by Habitual on 2012-05-27
> **haqking said:**
> None, dont conduct banking transactions on public (insecure) networks, the end ! ;-)

Amen to "The End";)

---

