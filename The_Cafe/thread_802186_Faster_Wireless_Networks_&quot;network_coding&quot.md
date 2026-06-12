---
title: "Faster Wireless Networks: &quot;network coding&quot; protocols..."
date: 2008-05-21
forum: The Cafe
---

### Post by Sporkman on 2008-05-21
[http://www.technologyreview.com/Infotech/20805/](http://www.technologyreview.com/Infotech/20805/)

> **Faster Wireless Networks**

Sending descriptions of data could be more efficient than sending the data itself.

By Duncan Graham-Rowe

The role of computer networks would appear to be fairly straightforward: to ferry data from one point to another. But a novel wireless-network protocol developed for the U.S. military breaks with this tradition by sending not the data itself but rather a description of the data. In simulations, a network using the protocol was five times more efficient than a traditional network. Within the next year, the U.S. Defense Advanced Research Projects Agency (DARPA) will test the protocol in field trials at FortA. P. Hill in Virginia.

The protocol is part of a project to create a new generation of mobile ad-hoc networks--self-configuring networks of mobile wireless nodes--that will enable faster and more reliable tactical communications between military personnel and vehicles, says Greg Lauer, section head for advanced network systems at BAE Systems in Burlington, MA, which helped develop the protocol for DARPA.

But the project also demonstrates the potential of a new and exciting field called network coding, says Muriel Médard, an associate professor of electrical engineering and computer science at MIT, who collaborated on the project with BAE Systems.

Network coding is a relatively young field, though there has been some interest in using it to make the Internet more efficient. Microsoft's peer-to-peer test bed Avalanche, for example, was designed to use network coding to deliver wide-scale on-demand TV and software patches without causing bottlenecks. But problems specific to mobile wireless networks are particularly amenable to solutions that use network coding.

In many ways, the analogy between the Internet and a superhighway is apt, Médard says. A lot of networks are built on a transportation model, with data traveling from address to address. "Data is transported very much like you would transport any other goods," says Médard. The trouble is that when you get a traffic jam, things grind to a halt.

"In a traditional network, you break information into packets and forward them between nodes," says Lauer. If a packet doesn't reach its destination, it will be sent and re-sent until its arrival is confirmed. But in some types of network, such as mobile wireless networks, there is a fairly high chance that the packets won't be received because of interference or limited bandwidth, or because a mobile node has wandered out of range or been destroyed. If nodes keep transmitting data until they receive confirmation, Lauer says, a bottleneck can result.

With network coding this is not an issue. "You take a group of packets and combine them," says Lauer. The result is a single packet that contains traces of information from each of the original packets. This hybrid packet is then sent to one or more additional nodes.

By itself, the hybrid packet just looks like gobbledegook, says Médard. But it includes a small amount of data that acts as a clue to its contents. A single packet won't normally contain enough clues to allow its data to be reconstructed. But as long as the destination node receives enough independent packets from enough different sources, it should be able to recover all the original data, Médard says.

The advantage of this is not only that you are using less bandwidth to send information, and thus avoiding bottlenecks, but also that you don't have to keep track of which node sent what, says Médard.

Surprisingly, even the means of combining data into a single packet at the source node doesn't have to be shared. If the packets contain enough clues, the destination nodes can reconstruct the contents of packets that have been created randomly. You're not sending data, per se, says Lauer, you're sending pieces of algorithms for assembling data.

Network coding is an offshoot of a field called information theory, which has already been put to use in data-compression software. But it's only relatively recently that people have started looking at how network coding could be used to send data. "It turns out it can be extremely powerful," Médard says.

As part of a program funded by DARPA, BAE and MIT used network-coding principles to develop protocols that could be used to send information to multiple destinations. In a conventional network, each node would act like a router, steering specific information toward specific destinations. But in BAE and DARPA's network, all nodes broadcast all information to all other nodes.

In the DARPA simulations, where a tactical mobile network was emulated on an Ethernet network, the researchers experimented to see how much they could reduce the bandwidth of the network while maintaining the same standard of communication. The simulations involved all forms of military data, from voice and video streams to tactical data, and all kinds of conditions, such as interference and poor connectivity.

The researchers found that they could reduce the bandwidth to just one-fifth of that required by a conventional network, with no loss of quality. The upcoming field tests, on the other hand, will investigate whether the protocols can be used to send more data over existing radio networks than standard protocols can, says Lauer.

Network coding is an exciting new area that has attracted a lot of interest, says Christina Fragouli, an expert in network coding at the École Polytechnique Fédérale de Lausanne in Switzerland. And mobile wireless networks are precisely the kind of application that network coding can help with, she says. "It's a very difficult kind of network to deal with," she says, because of its intrinsic interference problems and limited bandwidth.

The protocols have also been tested on a standard Wi-Fi network as a way to stream video, and the results were very promising, says Médard. Further down the line, network coding could help perform security functions. "There are ways to tell if someone has messed around with your data," Médard says.


---

