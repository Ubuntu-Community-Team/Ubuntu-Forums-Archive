---
title: "Give Bittorrent Option for Software Sources"
date: 2008-05-14
forum: Ubuntu Brainstorm
---

### Post by Megatog615 on 2008-05-14
Using debtorrent and apt-transport-debtorrent, it is possible to distribute binary packages with bittorrent. I use it on all of my systems to reduce load on the Ubuntu package archive. In my opinion, slowness on upgrade day can be reduced if users were given the option to download packages via bittorrent rather than from the archive. With debtorrent, packages are distributed via bittorrent if available, but falls back to http if the package cannot be retrieved from bittorrent. This ensures a guaranteed download.

Also, debtorrent could be enhanced with zeroconf capability to automatically add peers in a local area network to download packages from other computers in the local network. This would obsolete apt-proxy instantly, as the apt-proxy machine must be up 24/7(don't quote me on that, I have no experience with apt-proxy). This also reduces overall client bandwidth usage(on the internet), and eases upgrading of multiple machines on a network.

If a bittorrent option is created, give the user the ability to throttle the bandwidth usage of debtorrent(config files in /etc/debtorrent) in the software sources GUI. Have an extra tab just for bittorrent options appear when the bittorrent option is checkmarked, and put options such as "throttle upload speed," "throttle download speed," "do not throttle for local area network peers," and have checkmarks for each(throttles disabled when unchecked).

---

### Post by ghindo on 2008-05-14
+1

I had no idea that this option was even *available*.  I think the more Ubuntu and Canonical push BitTorrent as a means of distribution, the more positive a result.  It gives users choice, it reduces the stress on servers, and it helps legitimize BitTorrent as a means of distribution.

**Edit:**  Does debtorrent even *use* the BitTorrent protocol, or just a similar one of its own?

---

### Post by Megatog615 on 2008-05-14
Yes, it uses the bittorrent protocol. Debtorrent runs a tracker and client on your machine. The tracker seeds packages, and the client catches apt requests to the debtorrent:// protocol and uses a bittorrent wrapper to download. Anything it can't find in the swarm, it downloads from the actual repository.
Here's an example debtorrent:// line:
```
deb debtorrent://localhost:9988/us.archive.ubuntu.com/ubuntu/ hardy main
```
If it has to fall back to [http://,](http://,) it logically removes the debtorrent-related stuff and uses [http://,](http://,) like this:
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main
```
And you don't have to add that line. Just modify your sources.list to have debtorrent://localhost:9988/ instead of [http://.](http://.)

One thing: debtorrent can't download source packages yet so don't modify your deb-src lines. I'm not sure if debtorrent just automatically falls back to http:// for deb-src lines or not.

---

### Post by ghindo on 2008-05-14
Is there any GUI avaiable for debtorrent?  It may not be worth it to include by default into future versions of Ubuntu if it isn't easy for users to implement and control.

---

### Post by coolen on 2008-05-14
I really like this idea. I wrote a HowTo on using Apt-Cacher a while back. I'd love to integrate this. Have the server use DebTorrent, then other clients use Apt-Cacher. This would allow everyone to save bandwidth.

Do you know if DebTorrent can fulfill this on its own? You mentioned zeroconf capabilities, so I'm thinking it'd ask local hosts if they have a package, then fetch directly from them, or else go to the outside world. Am I right?

I had a moment earlier where my brother couldn't install anything on his machine. I wasn't home at the time, and I forgot that I'd turned my server off. I don't know if it's possible to make APT fall back to the direct access method, but something tells me it's not (I'm tearing my hair out trying to figure out how to disable the cache).

---

### Post by Megatog615 on 2008-05-14
[quote=ghindo]Is there any GUI avaiable for debtorrent? It may not be worth it to include by default into future versions of Ubuntu if it isn't easy for users to implement and control.[/quote]Debtorrent is transparent. Once it is activated, apt frontends(such as synaptic, aptitude, and update-manager) don't need to be configured to handle it.

[quote=coolen]Do you know if DebTorrent can fulfill this on its own? You mentioned zeroconf capabilities, so I'm thinking it'd ask local hosts if they have a package, then fetch directly from them, or else go to the outside world. Am I right?[/quote]Many bittorrent clients have options to enable Zeroconf, which is a protocol for enabling communication with local area network users by automatically discovering network peers. Debtorrent does not have this, and would benefit if it did.

[quote=coolen]I had a moment earlier where my brother couldn't install anything on his machine. I wasn't home at the time, and I forgot that I'd turned my server off. I don't know if it's possible to make APT fall back to the direct access method, but something tells me it's not (I'm tearing my hair out trying to figure out how to disable the cache).[/quote]Bittorrent works by connecting to peers to download parts of a file, then using a hash to check if the file is not corrupt. Using this basic principle, and the addition of Zeroconf, you could dist-upgrade one machine, then dist-upgrade the rest and they will connect to each other and download the latest packages over the network, and not even access the Internet. apt-proxy is basically the same idea, but the apt-proxy machine must be on 24/7 in order to serve other computers. With Debtorrent, every computer becomes a server of packages and doesn't have to be on 24/7 in order for the concept to work.

---

### Post by FuturePilot on 2008-05-14
The only bad thing I see about this is that some ISPs block torrent traffic. Also some will get mad if they notice you're seeding torrents 24/7

---

### Post by Megatog615 on 2008-05-14
> **FuturePilot said:**
> The only bad thing I see about this is that some ISPs block torrent traffic. Also some will get mad if they notice you're seeding torrents 24/7Which is why there would be an option to throttle seeding.
ISP's blocking bittorrent traffic is irrelevant since this is an option and not forced-function. This wouldn't even be default behaviour.

Also, I think Debtorrent only seeds when apt is running, so you're not seeding 24/7. If Zeroconf were implemented it should seed to network users regardless whether or not apt is running.

---

### Post by CarpKing on 2008-05-14
> **FuturePilot said:**
> The only bad thing I see about this is that some ISPs block torrent traffic. Also some will get mad if they notice you're seeding torrents 24/7

If bittorrent became known more for legitimate uses (such as system updates), this behavior would be less acceptable in the eyes of customers.  Currently ISPs are encouraged to take such steps.  

Also, this would be a godsend on release days, when torrenting the iso takes fifteen minutes but upgrading takes five+ hours.

---

### Post by coolen on 2008-05-15
> **Megatog615 said:**
> Bittorrent works by connecting to peers to download parts of a file, then using a hash to check if the file is not corrupt. Using this basic principle, and the addition of Zeroconf, you could dist-upgrade one machine, then dist-upgrade the rest and they will connect to each other and download the latest packages over the network, and not even access the Internet. apt-proxy is basically the same idea, but the apt-proxy machine must be on 24/7 in order to serve other computers. With Debtorrent, every computer becomes a server of packages and doesn't have to be on 24/7 in order for the concept to work.

Yeah. I'd definitely prefer the decentralised model of debtorrent. It would be fantastic for larger networks with many users coming and going (although if any exist which run enough Debian systems to make this useful is unknown to me).

---

