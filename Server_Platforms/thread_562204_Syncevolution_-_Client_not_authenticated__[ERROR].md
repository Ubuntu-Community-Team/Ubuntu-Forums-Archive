---
title: "Syncevolution - Client not authenticated  [ERROR]"
date: 2007-09-28
forum: Server Platforms
---

### Post by psykar on 2007-09-28
Hi, I installed SyncEvolution following the many tutorials here and there on the internet.
Installation went fine, copied and edited the configuration files.

Everything seems to run fine, except that I get the following error message:

```

12:57:04 GMT -0400 [INFO] - Synchronization URL: http://sync.scheduleworld.com/funambol/ds
12:57:04 GMT -0400 [INFO] - Preparing synchronization of addressbook...
12:57:04 GMT -0400 [INFO] - Preparing synchronization of calendar...
12:57:04 GMT -0400 [INFO] - Preparing synchronization of memo...
12:57:04 GMT -0400 [INFO] - Preparing synchronization of todo...
12:57:05 GMT -0400 [ERROR] - Error in preparing sync: Client not authenticated
12:57:05 GMT -0400 [ERROR] - sync failed without an error description, check log

Synchronization failed, see /tmp/SyncEvolution-user-scheduleworld/client.log for details.

```

Here it the log file:

```

12:57:04 GMT -0400 [INFO] - Synchronization URL: http://sync.scheduleworld.com/funambol/ds
12:57:04 GMT -0400 [INFO] - Preparing synchronization of addressbook...
12:57:04 GMT -0400 [INFO] - Preparing synchronization of calendar...
12:57:04 GMT -0400 [INFO] - Preparing synchronization of memo...
12:57:04 GMT -0400 [INFO] - Preparing synchronization of todo...
12:57:04 GMT -0400 [DEBUG] - devinfo: <DevInf xmlns="syncml:devinf"><VerDTD>1.1</VerDTD>
<Man>Patrick Ohly</Man>
<Mod>SyncEvolution</Mod>
<OEM>Open Source</OEM>
<SwV>0.6</SwV>
<DevID>psykar-laptop</DevID>
<DevTyp>workstation</DevTyp>
<UTC/><SupportLargeObjs/><DataStore><SourceRef>addressbook</SourceRef>
<Rx-Pref><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Rx>
<Rx><CTType>text/x-vcard</CTType>
<VerCT>2.1</VerCT>
</Rx>
<Tx-Pref><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Tx>
<Tx><CTType>text/x-vcard</CTType>
<VerCT>2.1</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
<DataStore><SourceRef>calendar</SourceRef>
<Rx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx>
<Tx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
<DataStore><SourceRef>memo</SourceRef>
<Rx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx>
<Tx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
<DataStore><SourceRef>todo</SourceRef>
<Rx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx>
<Tx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
</DevInf>

12:57:04 GMT -0400 [DEBUG] - devinfo hash: xDoIfLWvc+bUD1twINx0OA==
12:57:04 GMT -0400 [DEBUG] - devinfo changed, retransmit
12:57:04 GMT -0400 [DEBUG] - Initialization message:
12:57:04 GMT -0400 [DEBUG] - <?xml version="1.0" encoding="UTF-8"?>
<SyncML>
<SyncHdr><VerDTD>1.1</VerDTD>
<VerProto>SyncML/1.1</VerProto>
<SessionID>1190998624</SessionID>
<MsgID>1</MsgID>
<Target><LocURI>http://sync.scheduleworld.com/funambol/ds</LocURI>
</Target>
<Source><LocURI>psykar-laptop</LocURI>
<LocName>66180	</LocName>
</Source>
<Cred><Meta><Format xmlns="syncml:metinf">b64</Format>
<Type xmlns="syncml:metinf">syncml:auth-md5</Type>
</Meta>
<Data>4cI1cRZ0bcphZIpII4X8qA==</Data>
</Cred>
<Meta><MaxMsgSize xmlns="syncml:metinf">8192</MaxMsgSize>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</SyncHdr>
<SyncBody><Alert><CmdID>1</CmdID>
<Data>200</Data>
<Item><Target><LocURI>card3</LocURI>
</Target>
<Source><LocURI>addressbook</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998624</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Alert><CmdID>2</CmdID>
<Data>200</Data>
<Item><Target><LocURI>cal2</LocURI>
</Target>
<Source><LocURI>calendar</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998624</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Alert><CmdID>3</CmdID>
<Data>200</Data>
<Item><Target><LocURI>note</LocURI>
</Target>
<Source><LocURI>memo</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998624</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Alert><CmdID>4</CmdID>
<Data>200</Data>
<Item><Target><LocURI>task2</LocURI>
</Target>
<Source><LocURI>todo</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998624</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Put><CmdID>5</CmdID>
<Meta><Type xmlns="syncml:metinf">application/vnd.syncml-devinf+xml</Type>
</Meta>
<Item><Source><LocURI>./devinf11</LocURI>
</Source>
<Data><DevInf xmlns="syncml:devinf"><VerDTD>1.1</VerDTD>
<Man>Patrick Ohly</Man>
<Mod>SyncEvolution</Mod>
<OEM>Open Source</OEM>
<SwV>0.6</SwV>
<DevID>psykar-laptop</DevID>
<DevTyp>workstation</DevTyp>
<UTC/><SupportLargeObjs/><DataStore><SourceRef>addressbook</SourceRef>
<Rx-Pref><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Rx>
<Rx><CTType>text/x-vcard</CTType>
<VerCT>2.1</VerCT>
</Rx>
<Tx-Pref><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/vcard</CTType>
<VerCT>3.0</VerCT>
</Tx>
<Tx><CTType>text/x-vcard</CTType>
<VerCT>2.1</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
<DataStore><SourceRef>calendar</SourceRef>
<Rx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx>
<Tx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
<DataStore><SourceRef>memo</SourceRef>
<Rx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx>
<Tx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
<DataStore><SourceRef>todo</SourceRef>
<Rx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx-Pref>
<Rx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Rx>
<Tx-Pref><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx-Pref>
<Tx><CTType>text/calendar</CTType>
<VerCT>2.0</VerCT>
</Tx>
<SyncCap><SyncType>2</SyncType>
<SyncType>1</SyncType>
<SyncType>4</SyncType>
<SyncType>6</SyncType>
<SyncType>3</SyncType>
<SyncType>5</SyncType>
</SyncCap>
</DataStore>
</DevInf>
</Data>
</Item>
</Put>
<Final/></SyncBody>
</SyncML>
12:57:04 GMT -0400 [DEBUG] - User Agent = SyncEvolution
12:57:04 GMT -0400 [DEBUG] - Requesting resource /funambol/ds at sync.scheduleworld.com:80
12:57:04 GMT -0400 [DEBUG] - libcurl info: About to connect() to sync.scheduleworld.com port 80
12:57:04 GMT -0400 [DEBUG] - libcurl info:   Trying 72.51.41.97... 
12:57:04 GMT -0400 [DEBUG] - libcurl info: connected
12:57:04 GMT -0400 [DEBUG] - libcurl info: Connected to sync.scheduleworld.com (72.51.41.97) port 80
12:57:04 GMT -0400 [DEBUG] - libcurl header out:
POST /funambol/ds HTTP/1.1

User-Agent: SyncEvolution

Host: sync.scheduleworld.com

Accept: */*

Content-Type: application/vnd.syncml+xml

Content-Length: 4234

Expect: 100-continue



12:57:04 GMT -0400 [DEBUG] - libcurl header in: HTTP/1.1 100 Continue

12:57:05 GMT -0400 [DEBUG] - libcurl header in: HTTP/1.1 200 OK

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Server: Apache-Coyote/1.1

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Set-Cookie: JSESSIONID=BB31FFD2ADE6B49989FA2AD7927081D5; Path=/funambol

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Content-Type: application/vnd.syncml+xml

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Content-Length: 1628

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Date: Fri, 28 Sep 2007 16:57:15 GMT

12:57:05 GMT -0400 [DEBUG] - libcurl info: Connection #0 to host sync.scheduleworld.com left intact
12:57:05 GMT -0400 [DEBUG] - <?xml version="1.0" encoding="UTF-8"?>
<SyncML>
<SyncHdr>
<VerDTD>1.1</VerDTD>
<VerProto>SyncML/1.1</VerProto>
<SessionID>1190998624</SessionID>
<MsgID>1</MsgID>
<Target>
<LocURI>psykar-laptop</LocURI>
<LocName>66180	</LocName>
</Target>
<Source>
<LocURI>http://sync.scheduleworld.com/funambol/ds</LocURI>
</Source>
<RespURI>http://sync.scheduleworld.com/funambol/ds;jsessionid=BB31FFD2ADE6B49989FA2AD7927081D5</RespURI>
</SyncHdr>
<SyncBody>
<Status>
<CmdID>1</CmdID>
<MsgRef>1</MsgRef>
<CmdRef>0</CmdRef>
<Cmd>SyncHdr</Cmd>
<TargetRef>http://sync.scheduleworld.com/funambol/ds</TargetRef>
<SourceRef>psykar-laptop</SourceRef>
<Chal>
<Meta>
<Format xmlns='syncml:metinf'>b64</Format>
<Type xmlns='syncml:metinf'>syncml:auth-basic</Type>
</Meta>
</Chal>
<Data>401</Data>
</Status>
<Status>
<CmdID>2</CmdID>
<MsgRef>1</MsgRef>
<CmdRef>1</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>card3</TargetRef>
<SourceRef>addressbook</SourceRef>
<Data>401</Data>
</Status>
<Status>
<CmdID>3</CmdID>
<MsgRef>1</MsgRef>
<CmdRef>2</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>cal2</TargetRef>
<SourceRef>calendar</SourceRef>
<Data>401</Data>
</Status>
<Status>
<CmdID>4</CmdID>
<MsgRef>1</MsgRef>
<CmdRef>3</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>note</TargetRef>
<SourceRef>memo</SourceRef>
<Data>401</Data>
</Status>
<Status>
<CmdID>5</CmdID>
<MsgRef>1</MsgRef>
<CmdRef>4</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>task2</TargetRef>
<SourceRef>todo</SourceRef>
<Data>401</Data>
</Status>
<Status>
<CmdID>6</CmdID>
<MsgRef>1</MsgRef>
<CmdRef>5</CmdRef>
<Cmd>Put</Cmd>
<SourceRef>./devinf11</SourceRef>
<Data>401</Data>
</Status>
<Final></Final>
</SyncBody>
</SyncML>

12:57:05 GMT -0400 [DEBUG] - Response read
12:57:05 GMT -0400 [DEBUG] - Initialization message:
12:57:05 GMT -0400 [DEBUG] - <?xml version="1.0" encoding="UTF-8"?>
<SyncML>
<SyncHdr><VerDTD>1.1</VerDTD>
<VerProto>SyncML/1.1</VerProto>
<SessionID>1190998624</SessionID>
<MsgID>2</MsgID>
<Target><LocURI>http://sync.scheduleworld.com/funambol/ds</LocURI>
</Target>
<Source><LocURI>psykar-laptop</LocURI>
</Source>
<Cred><Meta><Format xmlns="syncml:metinf">b64</Format>
<Type xmlns="syncml:metinf">syncml:auth-basic</Type>
</Meta>
<Data>NjYxODAJOnphcXhzdw==</Data>
</Cred>
<Meta><MaxMsgSize xmlns="syncml:metinf">8192</MaxMsgSize>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</SyncHdr>
<SyncBody><Status><CmdID>1</CmdID>
<MsgRef>1</MsgRef>
<CmdRef>0</CmdRef>
<Cmd>SyncHdr</Cmd>
<TargetRef>http://sync.scheduleworld.com/funambol/ds</TargetRef>
<SourceRef>psykar-laptop</SourceRef>
<Data>200</Data>
</Status>
<Alert><CmdID>2</CmdID>
<Data>200</Data>
<Item><Target><LocURI>card3</LocURI>
</Target>
<Source><LocURI>addressbook</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998625</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Alert><CmdID>3</CmdID>
<Data>200</Data>
<Item><Target><LocURI>cal2</LocURI>
</Target>
<Source><LocURI>calendar</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998625</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Alert><CmdID>4</CmdID>
<Data>200</Data>
<Item><Target><LocURI>note</LocURI>
</Target>
<Source><LocURI>memo</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998625</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Alert><CmdID>5</CmdID>
<Data>200</Data>
<Item><Target><LocURI>task2</LocURI>
</Target>
<Source><LocURI>todo</LocURI>
</Source>
<Meta><Anchor xmlns="syncml:metinf"><Last>0</Last>
<Next>1190998625</Next>
</Anchor>
<MaxObjSize xmlns="syncml:metinf">500000</MaxObjSize>
</Meta>
</Item>
</Alert>
<Final/></SyncBody>
</SyncML>
12:57:05 GMT -0400 [DEBUG] - Requesting resource /funambol/ds;jsessionid=BB31FFD2ADE6B49989FA2AD7927081D5 at sync.scheduleworld.com:80
12:57:05 GMT -0400 [DEBUG] - libcurl info: Re-using existing connection! (#0) with host sync.scheduleworld.com
12:57:05 GMT -0400 [DEBUG] - libcurl info: Connected to sync.scheduleworld.com (72.51.41.97) port 80
12:57:05 GMT -0400 [DEBUG] - libcurl header out:
POST /funambol/ds;jsessionid=BB31FFD2ADE6B49989FA2AD7927081D5 HTTP/1.1

User-Agent: SyncEvolution

Host: sync.scheduleworld.com

Accept: */*

Content-Type: application/vnd.syncml+xml

Content-Length: 2003

Expect: 100-continue



12:57:05 GMT -0400 [DEBUG] - libcurl header in: HTTP/1.1 100 Continue

12:57:05 GMT -0400 [DEBUG] - libcurl header in: HTTP/1.1 200 OK

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Server: Apache-Coyote/1.1

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Content-Type: application/vnd.syncml+xml

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Content-Length: 1462

12:57:05 GMT -0400 [DEBUG] - libcurl header in: Date: Fri, 28 Sep 2007 16:57:15 GMT

12:57:05 GMT -0400 [DEBUG] - libcurl info: Connection #0 to host sync.scheduleworld.com left intact
12:57:05 GMT -0400 [DEBUG] - <?xml version="1.0" encoding="UTF-8"?>
<SyncML>
<SyncHdr>
<VerDTD>1.1</VerDTD>
<VerProto>SyncML/1.1</VerProto>
<SessionID>1190998624</SessionID>
<MsgID>2</MsgID>
<Target>
<LocURI>psykar-laptop</LocURI>
</Target>
<Source>
<LocURI>http://sync.scheduleworld.com/funambol/ds</LocURI>
</Source>
<RespURI>http://sync.scheduleworld.com/funambol/ds;jsessionid=BB31FFD2ADE6B49989FA2AD7927081D5</RespURI>
</SyncHdr>
<SyncBody>
<Status>
<CmdID>1</CmdID>
<MsgRef>2</MsgRef>
<CmdRef>0</CmdRef>
<Cmd>SyncHdr</Cmd>
<TargetRef>http://sync.scheduleworld.com/funambol/ds</TargetRef>
<SourceRef>psykar-laptop</SourceRef>
<Chal>
<Meta>
<Format xmlns='syncml:metinf'>b64</Format>
<Type xmlns='syncml:metinf'>syncml:auth-basic</Type>
</Meta>
</Chal>
<Data>401</Data>
</Status>
<Status>
<CmdID>2</CmdID>
<MsgRef>2</MsgRef>
<CmdRef>2</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>card3</TargetRef>
<SourceRef>addressbook</SourceRef>
<Data>401</Data>
</Status>
<Status>
<CmdID>3</CmdID>
<MsgRef>2</MsgRef>
<CmdRef>3</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>cal2</TargetRef>
<SourceRef>calendar</SourceRef>
<Data>401</Data>
</Status>
<Status>
<CmdID>4</CmdID>
<MsgRef>2</MsgRef>
<CmdRef>4</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>note</TargetRef>
<SourceRef>memo</SourceRef>
<Data>401</Data>
</Status>
<Status>
<CmdID>5</CmdID>
<MsgRef>2</MsgRef>
<CmdRef>5</CmdRef>
<Cmd>Alert</Cmd>
<TargetRef>task2</TargetRef>
<SourceRef>todo</SourceRef>
<Data>401</Data>
</Status>
<Final></Final>
</SyncBody>
</SyncML>

12:57:05 GMT -0400 [DEBUG] - Response read
12:57:05 GMT -0400 [ERROR] - Error in preparing sync: Client not authenticated
12:57:05 GMT -0400 [DEBUG] - libcurl info: Closing connection #0
12:57:05 GMT -0400 [DEBUG] - Writing configuration settings to the management tree
12:57:05 GMT -0400 [ERROR] - sync failed without an error description, check log

```
[SIZE="4"]
I believe the source of the error lies in the ~/.sync4j/evolution/scheduleworld/spds/syncml/config.txt configuration file[/SIZE]

```

# the base URL of the SyncML server:
# - Sync4j 2.3
#syncURL = http://localhost:8080/sync4j/sync
# - Funambol >= 3.0
#syncURL = http://localhost:8080/funambol/ds
# - sync.scheduleworld.com
syncURL = http://sync.scheduleworld.com/funambol/ds

# the SyncML server gets this string and will use it to keep track of
# changes that still need to be synchronized with this particular
# client; it must be set to something unique if SyncEvolution is used
# to synchronize data between different computers
deviceId = psykar-laptop

# authorization for the SyncML server
username = (my user name)
password = (my password)

# set to T to enable an HTTP proxy
useProxy = 0
# proxy URL (http://<host>:<port>)
proxyHost = 
# user agent string used for HTTP
userAgent = SyncEvolution

# full path to directory where automatic backups and logs
# are stored for all synchronizations; if empty, the temporary
# directory "$TMPDIR/SyncEvolution-<username>-<server>" will
# be used to keep the data of just the latest synchronization run;
# if "none", then no backups of the databases are made and any
# output is printed directly instead of writing it into a log
#
# When writing into a log nothing will be shown during the
# synchronization. Instead the important messages are extracted
# automatically from the log at the end.
logdir =

# level of detail for log messages:
# - 0 (or unset) = INFO messages without log file, DEBUG with log file
# - 1 = only ERROR messages
# - 2 = also INFO messages
# - 3 = also DEBUG messages
loglevel = 0

# Unless this option is set, SyncEvolution will never delete
# anything in the "logdir". If set, the oldest directories and
# all their content will be removed after a successful sync
# to prevent the number of log directories from growing beyond
# the given limit.
maxlogdirs = 5

# Support for large objects and limiting the message size was added in
# SyncEvolution 0.5, but still disabled in the example configurations
# of that version. Some servers had problems with that configuration,
# so now both features are enabled by default and it is recommended
# to update existing configurations.
#
# The maximum size of each message can be set (maxMsgSize) and the
# server can be told to never sent items larger than a certain
# threshold (maxObjSize). Presumably the server has to truncate or
# skip larger items. Finally the client and server may be given the
# permission to transmit large items in multiple messages (loSupport =
# large object support).
maxMsgSize = 8192
maxObjSize = 500000
loSupport = 1

# used by the SyncML library internally; do not modify
begin =1190998624
end =0
firstTimeSyncMode = 0
serverID = 
serverPWD = 
serverNonce = 
clientNonce = 
clientAuthType = 
serverAuthType = 
isServerAuthRequired = 0
proxyPort = 0
proxyUsername = 
proxyPassword = 
checkConn = 0
responseTimeout = 0
readBufferSize = 0
enableCompression = 0

```


Any help would be greatly appreciated,
Psykar

---

