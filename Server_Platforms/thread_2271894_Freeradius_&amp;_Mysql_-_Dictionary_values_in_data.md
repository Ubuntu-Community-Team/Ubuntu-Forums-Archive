---
title: "Freeradius &amp; Mysql - Dictionary values in database"
date: 2015-04-02
forum: Server Platforms
---

### Post by prldoyle on 2015-04-02
Hi. Sorry if this is not the correct place for posting this, I am new to the forum. 

I have successfully built a freeradius server  with MYSQL on ubuntu and using it for accounting. I have an Ingate SBC which is sending accounting information to the radius server. 

Each call is successfully added to the file in /var/log/freeradius/radacct/ and it contains all the information included in the ingate dictionary. The call is also present in the mysql database radacct. But none of the specific ingate data is in the database. What would I need to do to add this accounting information to the database. 

So the data contained in the radacct text file: 

Wed Apr  1 16:41:11 2015
	User-Name = "sip:xxxxxxxx@xxx.xxx.xxx.xxx"
	NAS-IP-Address = xxx.xxx.xxx.xxx
	Acct-Session-Id = "30001458-3636891656-390486@xxx.xxxxxxxxx.com_B2BUA_68191e91416xxx92cf09d84c3e72f0@sipgt-56c5a7d3"
	Acct-Status-Type = Stop
	Called-Station-Id = "sip:xxxxxxxx@xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx"
	Calling-Station-Id = "sip:xxxxxxxxx@xxxxxxxx@xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx"
	Acct-Session-Time = 9
	Acct-Terminate-Cause = User-Request
	Acct-Input-Octets = 76200
	Acct-Output-Octets = 86600
	Acct-Input-Packets = 381
	Acct-Output-Packets = 433
	IG-Acct-Input-Jitter = 0
	IG-Acct-Output-Jitter = 0
	IG-Acct-Input-Jitter-Max = 0
	IG-Acct-Output-Jitter-Max = 1
	IG-Acct-Input-Missing = 0
	IG-Acct-Output-Missing = 0
	IG-Acct-Input-Missing-Max = 0
	IG-Acct-Output-Missing-Max = 0
	IG-Acct-Input-Est-Mos = 440
	IG-Acct-Output-Est-Mos = 440
	IG-Acct-Input-Last-Payload-Type = 0
	IG-Acct-Output-Last-Payload-Type = 0
	IG-Acct-Input-Reordered = 0
	IG-Acct-Output-Reordered = 0
	IG-Acct-Input-Comfort-Noise = "No"
	IG-Acct-Output-Comfort-Noise = "No"
	IG-Acct-Input-Codec-Name = "PCMU"
	IG-Acct-Output-Codec-Name = "PCMU"
	IG-Acct-Input-DscpIn = 0
	IG-Acct-Input-DscpOut = 0
	IG-Acct-Output-DscpIn = 46
	IG-Acct-Output-DscpOut = 46
	IG-Acct-Input-IfIpIn = "172.16.2.202"
	IG-Acct-Input-IfIpOut = "xxx.xxx.xxx.xxx"
	IG-Acct-Output-IfIpIn = "xxx.xxx.xxx.xxx"
	IG-Acct-Output-IfIpOut = "172.16.2.202"
	IG-Acct-Input-Mtype = "audio RTP/AVP"
	IG-Acct-Output-Mtype = "audio RTP/AVP"
	Acct-Unique-Session-Id = "caf84fc7839f9a1e"
	Timestamp = 1427902871
	Request-Authenticator = Verified

the data contained in the radacct mysql table:

radacctid	 = 	1
acctsessionid	 = 	[email]30479778-3636967837-611833@xxx.xxxxxxx.com[/email]_B2BUA_293a3419
acctuniqueid	 = 	9d41b160088de305
username	 = 	sip:xxxxxxxxxxx@xxx.xxx.xxx.xxx 
groupname	 = 	
realm	 = 	
nasipaddress	 = 	172.16.2.202
nasportid	 = 	
nasporttype	 = 	
acctstarttime	 = 	02/04/15 13:50
acctstoptime	 = 	NULL
acctsessiontime	 = 	0
acctauthentic	 = 	
connectinfo_start	 = 	
connectinfo_stop	 = 	
acctinputoctets	 = 	0
acctoutputoctets	 = 	0
calledstationid	 = 	sip:xxxxxxxxxx@xxx.xxx.xxx.xxx  xxx.xxx.xxx.xxx 
callingstationid	 = 	sip:xxxxxxxxxxx@xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx 
acctterminatecause	 = 	
servicetype	 = 	
framedprotocol	 = 	
framedipaddress	 = 	
acctstartdelay	 = 	0
acctstopdelay	 = 	0


So basically my question is how do I add fields like IG-Acct-Input-Est-Mos to the database and have them populated by free radius. (just adding them in the database doesn't work!)

Any help would be very much appreciated.

---

### Post by prldoyle on 2015-04-02
I have found the answer, after lots of looking i have found the SQL script radius called to update the table. it is located in: /etc/freeradius/sql/mysql/dialup.conf

it needs modifiying to insert the specific values. Here is an example for adding IG-Acct-Input-Est-Mos

accounting_stop_query_alt = " \
          INSERT INTO ${acct_table2} \
            (acctsessionid, acctuniqueid, username, \
             realm, nasipaddress, nasportid, \
             nasporttype, acctstarttime, acctstoptime, \
             acctsessiontime, acctauthentic, connectinfo_start, \
             connectinfo_stop, acctinputoctets, acctoutputoctets, \
             calledstationid, callingstationid, acctterminatecause, \
             servicetype, framedprotocol, framedipaddress, \
             acctstartdelay, acctstopdelay,** IGAcctInputEstMos)** \
          VALUES \
            ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}', \
             '%{SQL-User-Name}', \
             '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}', \
             '%{NAS-Port-Type}', \
             DATE_SUB('%S', \
                 INTERVAL (%{%{Acct-Session-Time}:-0} + \
                 %{%{Acct-Delay-Time}:-0}) SECOND), \
             '%S', '%{Acct-Session-Time}', '%{Acct-Authentic}', '', \
             '%{Connect-Info}', \
             '%{%{Acct-Input-Gigawords}:-0}' << 32 | \
             '%{%{Acct-Input-Octets}:-0}', \
             '%{%{Acct-Output-Gigawords}:-0}' << 32 | \
             '%{%{Acct-Output-Octets}:-0}', \
             '%{Called-Station-Id}', '%{Calling-Station-Id}', \
             '%{Acct-Terminate-Cause}', \
             '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}', \
             '0', '%{%{Acct-Delay-Time}:-0}', **%{IG-Acct-Input-Est-Mos})**"

Thanks

---

