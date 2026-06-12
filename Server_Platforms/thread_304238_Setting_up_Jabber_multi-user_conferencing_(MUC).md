---
title: "Setting up Jabber multi-user conferencing (MUC)"
date: 2006-11-21
forum: Server Platforms
---

### Post by rbdavis on 2006-11-21
I have succesfully installed Jabber 1.4.3 and jabber-muc using apt-get.

My Jabber server is running and i can log in using a Jabber client.

However I can't access the MUC features.

I tried adding a service to jabber.xml:

<service id='conference.localhost'>
  <load><conference>/usr/lib/jabber/mu-conference/mu-conference.so</conference></load>
  <conference xmlns="jabber:config:conference">
    <public/>
	<sadmin>my.email.address@domain.com</sadmin>
    <vCard>
      <FN>Public Chatrooms</FN>
      <DESC>This service is for public chatrooms.</DESC>
      <URL>http://conference.localhost/logs/</URL>
    </vCard>
    <history>20</history>
    <notice>
      <join> has arrived</join>
      <leave> has left</leave>
      <rename> is now known as </rename>
    </notice>
	<dynamic/>
	<logdir>./logs/muc/</logdir>
  </conference>
</service>

And also added an item to the Jabber Browsing:

		<item category="conference" type="public" jid="conference.localhost" name="Public Conferencing" version="0.3">
		  <ns>jabber:iq:register</ns>
		  <ns>gc-1.0</ns>
		  <ns>http://jabber.org/protocol/muc</ns>
		</item>

However, whenever i try to create a room on conference.localhost, Exodus gives an error: "Room has been destroyed for an unknown reason".

Note: i am running Jabber on a local network.

---

