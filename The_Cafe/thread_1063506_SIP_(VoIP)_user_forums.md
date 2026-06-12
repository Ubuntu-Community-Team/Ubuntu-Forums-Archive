---
title: "SIP (VoIP) user forums?"
date: 2009-02-07
forum: The Cafe
---

### Post by jordon on 2009-02-07
I use Ekiga, and it's a pretty good piece of VoIP software, but I have one issue: I don't know anyone who uses it!

Skype has very active forums, including a "Skype Me" forum where people can ask to be called. From within the program, you can also search for users who have their status set to "Skype Me". Ekiga's search function doesn't seem to work too well, and there are no forums that I know of.

So, are there any forums for SIP users who want to be called?

---

### Post by bobone1 on 2009-05-30
[COLOR=#000000][FONT=Verdana]SIP is very much like HTTP, the Web protocol, or SMTP. Messages consist of headers and a message body. SIP message bodies for phone calls are defined in [SDP -the session description protocol]("http://ubuntuforums.org/wiki/view/SDP"). 


[LIST]
[*]SIP is a text-based protocol that uses UTF-8 encoding
[*]SIP uses port 5060 both for UDP and TCP. SIP may use other [transports]("http://ubuntuforums.org/wiki/view/SIP+transports")
[/LIST]
SIP offers all potentialities of the common [[COLOR=black]Internet Telephony[/COLOR]]("http://ubuntuforums.org/wiki/view/Internet+Telephony") features like: 

[LIST]
[*]call or media transfer
[*]call conference
[*]call hold
[/LIST]
Since SIP is a flexible protocol, it is possible to add more features and keep downward interoperability. 

SIP also does suffer from NAT or firewall restrictions. (Refer to [NAT and VOIP]("http://ubuntuforums.org/wiki/view/NAT+and+VOIP")) 

SIP can be regarded as the enabler protocol for telephony and voice over IP (VoIP) services. The following features of SIP play a major role in the enablement of IP telephony and VoIP: 


[LIST]
[*]Name Translation and User Location: Ensuring that the call reaches the called party wherever they are located. Carrying out any mapping of descriptive information to location information. Ensuring that details of the nature of the call (Session) are supported.
[*]Feature Negotiation: This allows the group involved in a call (this may be a multi-party call) to agree on the features supported Ã¢ï¿½ï¿½ recognizing that not all the parties can support the same level of features. For example video may or may not be supported; as any form of MIME type is supported by SIP, there is plenty of scope for negotiation.
[*]Call Participant Management: During a call a participant can bring other users onto the call or cancel connections to other users. In addition, users could be transferred or placed on hold.
[*]Call feature changes: A user should be able to change the call characteristics during the course of the call. For example, a call may have been set up as 'voice-only', but in the course of the call, the users may need to enable a video function. A third party joining a call may require different features to be enabled in order to participate in the call
[*]Media negotiation: The inherent SIP mechanisms that enable negotiation of the media used in a call, enable selection of the appropriate codec for establishing a call between the various devices. This way, less advanced devices can participate in the call, provided the appropriate codec is selected.
[/LIST][/FONT][/COLOR] 
I just recently updated from Voip Sip SDK - The easiest way to add dial and receive phone calls features to your applications they provide really good service. [http://www.voipsipsdk.com]("http://www.voipsipsdk.com/")

---

### Post by webmerlion on 2009-06-06
VOIP SIP SDK TOOLKIT HOME is new software for SIP for more details see my signature or this url [http://www.voipsipsdk.com/](http://www.voipsipsdk.com/)

---

