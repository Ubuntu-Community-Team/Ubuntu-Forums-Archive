---
title: "Unexplained TCP behavior - Ubuntu 13.10 and Ubuntu 12.04 LTS"
date: 2014-04-15
forum: Security
---

### Post by paul120 on 2014-04-15
I am using Scapy to analyze the behavior of various TCP implementations (Windows 8, 7, Ubuntu 13.10, 12.04). Scapy is a tool that can allows you to craft packets with send them over the network and receive responses. In the context of analyzing network protocols, Scapy is useful since you can send bad packets (with bad SYN/ACK numbers) and see how the implementation responds.

My setup consists of a Scapy guided client and a server which listens for incoming connections and does nothing with them. So far, I have done successful handshakes, terminations and all that but no data transfer and have tried to avoid most intricate details of TCP. I have also analyzed responses to bad requests (requests that had bad SEQ/ACK numbers or flags) which led me to a behavior I find hard to explain. The scenario is as follows: 

```


client ---- SYN [COLOR=#800000]0[/COLOR] _ ---> server 
[LISTENING] 
client <- SYN+ACK [COLOR=#800000]0[/COLOR] [COLOR=#800000]1[/COLOR] -- server [SYN_RCVD]

client -- ACK+FIN [COLOR=#800000]1[/COLOR] [COLOR=#800000]1[/COLOR] -> server [SYN_RCVD]
client <--- ACK [COLOR=#800000]1[/COLOR] [COLOR=#800000]2[/COLOR] ---- server [CLOSE_WAIT]

client ---- ACK [COLOR=#800000]1[/COLOR] [COLOR=#800000]20[/COLOR] --> server [CLOSE_WAIT]
client <--- ACK [COLOR=#800000]1[/COLOR] [COLOR=#800000]2[/COLOR] ---- server [CLOSE_WAIT] [COLOR=#00008B]or[/COLOR] no_response [CLOSE_WAIT]

```


*taken from my post on StackOverflow
Basically, whenever the server is in CLOSE_WAIT state and it receives a bad ACK (acknowledging a non existing packet), it eithers sends an ACK, retransmitting the ACK it sent for the ACK+FIN packet, or it sends nothing. I can't find any reason for this behavior nor can I see a pattern on when it sends the ACK and when it doesn't. I use Wireshark to monitor sent packets, perhaps Wireshark fails to detect some packets? I attached here a screenshot of several test runs, as shown in Wireshark. For each test ran, I used a different port on the client side, while the server remains the same. This behavior is present in both Ubuntu 12.04 and 13.10.
[ATTACH=CONFIG]252083[/ATTACH]
If anyone has suggestions on why the server behaves like this or if there is a parameter that might alter this, please let me know. BTW, the server is running on default settings (i.e. I didn't alter any parameters) and it does nothing on accepting a new socket.
BTW, if anyone is interested in such experiments, I can happily share details on the software that we built over Scapy to check the behavior.

Thanks bunch, Paul.

---

### Post by paul120 on 2014-07-17
I found the reason to anyone interested. It is all down to the snippet in the linux code for ack number processing. (taken from here [http://lxr.free-electrons.com/source/net/ipv4/tcp_input.c#L3358](http://lxr.free-electrons.com/source/net/ipv4/tcp_input.c#L3358))
```
 /* If the ack is older than previous acks * then we can probably ignore it.
 */
if (before(ack, prior_snd_una)) {
        /* RFC 5961 5.2 [Blind Data Injection Attack].[Mitigation] */
        if (before(ack, prior_snd_una - tp->max_window)) {
                tcp_send_challenge_ack(sk);
                return -1;
        }
        goto old_ack;
}


/* If the ack includes data we haven't sent yet, discard
 * this segment (RFC793 Section 3.9).
 */
if (after(ack, tp->snd_nxt))
        goto invalid_ack;

```

The scenario presented in my previous post would fall in the goto invalid_ack branch, case in which, no ack is sent. The interpretation of RFC 793 is wrong as an ACK SHOULD be sent for unacceptable acknowledgement numbers. Not that it makes much difference.

---

### Post by clearski on 2014-07-17
Why do you say that an ACK should be sent for unaccepted numbers? Even in figure 11 of the RFC 793 (posted below), client A doesn't reply with an ACK to server B, which continues to request data without knowing that A is down, but instead it sends a RST. Since there isn't a connection anymore, there's nothing to acknowledge to B, because what B just did - from the perspective of A - was to send data without having an established connection. If ACK should be used anyway, the SYN flag in the TCP protocol is useless.

To me it seems at least reasonable not to acknowledge a) any segment which has already been received and acknowledged or b) a segment which is out of order:

- client A receives from server B an ACK for a segment which hasn't been sent yet (window size: 1000; client A sent 1000 bytes having SEQ 2001 and just receives from B ACK for 8001)
- client A receives an ACK for a segment which has already been sent and acknowledged
- server B receives a SEQ 6001 when he just requested SEQ2001 using a window size of 1000, for example.

Nothing wrong with the interpretation of the RFC in the Linux code, imho.


***

        ```
TCP A                                              TCP B

  1.  (CRASH)                                   (send 300,receive 100)

  2.  (??)    <-- <SEQ=300><ACK=100><DATA=10><CTL=ACK> <-- ESTABLISHED

  3.          --> <SEQ=100><CTL=RST>                   --> (ABORT!!)

           Active Side Causes Half-Open Connection Discovery

                               Figure 11.
```

---

