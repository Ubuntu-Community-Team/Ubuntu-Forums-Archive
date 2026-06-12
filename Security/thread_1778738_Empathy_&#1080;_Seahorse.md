---
title: "Empathy &#1080; Seahorse"
date: 2011-06-09
forum: Security
---

### Post by go8765 on 2011-06-09
Hello. I have i little problem with empathy and seahorse: when i try to make icq account empathy make new seahorse key. can i make acoount without this key, because i dont want to unlock it every time when i run empathy.
p.s. when i try to make empty password in seahorse key - i cant push button that confirm making emty password...

---

### Post by go8765 on 2011-06-11
i remove seahorse. but now empathy forbot after restart my isq account.
and i hawe another trouble - i cant connect to icq with empathy

---

### Post by t.rei on 2011-06-11
This not being able to connect to icq... I think that might be a problem with icq, because I have the very same problem of just getting a network error.

---

### Post by 3vi1 on 2011-06-11
I can't get empathy to connect to ICQ either at the moment.  I'm thinking server-side issues or changes are going on.

---

### Post by t.rei on 2011-06-12
It's working without problems using pidgin or kopete - So this is a pure empathy/telepathy problem, it seems.

---

### Post by go8765 on 2011-06-13
> **t.rei said:**
> It's working without problems using pidgin or kopete - So this is a pure empathy/telepathy problem, it seems.

i fix it by using jabber transport icq...

---

### Post by player999 on 2011-06-15
go8765, your solution is wicked!
After working with Seahorse(generated key) i getting "Network problem". I am using ICQ protocol. Change of login sockets does not help.
Yeah, i think too that this is telepathy/dbus problem. But wondering what should i do to get it work. Here is debugger messages.
```

mcd-DEBUG: 06/16/2011 00:02:33.994554: account_reconnect: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.994615: _mcd_connection_release_tp_connection: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.994664: _mcd_account_set_connection_status: haze/icq/_33456106010: 2 because 1
mcd-DEBUG: 06/16/2011 00:02:33.994702: mcd_account_freeze_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.994788: _mcd_account_set_connection_status: changing detailed D-Bus error from 'org.freedesktop.Telepathy.Error.NetworkError' to ''
mcd-DEBUG: 06/16/2011 00:02:33.994826: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 06/16/2011 00:02:33.994868: mcd_account_changed_property: called: Connection
mcd-DEBUG: 06/16/2011 00:02:33.994903: mcd_account_changed_property: First changed property
mcd-DEBUG: 06/16/2011 00:02:33.995129: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 06/16/2011 00:02:33.995173: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 06/16/2011 00:02:33.995210: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 06/16/2011 00:02:33.995255: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 06/16/2011 00:02:33.995297: mcd_account_thaw_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.995335: emit_property_changed: called
mcd-DEBUG: 06/16/2011 00:02:33.995451: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 06/16/2011 00:02:33.995492: on_connection_abort: called (0x1ec90d0, account haze/icq/_33456106010)
mcd-DEBUG: 06/16/2011 00:02:33.995538: _mcd_mission_set_parent: child = 0x1ec90d0, parent = (nil)
mcd-DEBUG: 06/16/2011 00:02:33.995580: _mcd_operation_remove_mission: removing mission: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995618: _mcd_connection_dispose: called for object 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995655: _mcd_connection_release_tp_connection: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995697: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 06/16/2011 00:02:33.995734: _mcd_mission_dispose: mission disposed 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995774: mcd_dispatcher_lost_connection: 0x1ec2830: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995810: mcd_dispatcher_lost_connection: 0x1ec2830: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995846: mcd_dispatcher_lost_connection: 0x1ec2830: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995882: mcd_dispatcher_lost_connection: 0x1ec2830: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995923: mcd_dispatcher_lost_connection: 0x1ec2830: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.995959: mcd_dispatcher_lost_connection: 0x1ec2830: 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.996000: _mcd_mission_finalize: mission finalized 0x1ec90d0
mcd-DEBUG: 06/16/2011 00:02:33.996041: _mcd_account_dup_parameters: called
mcd-DEBUG: 06/16/2011 00:02:33.996161: _mcd_mission_set_parent: child = 0x1ec9250, parent = 0x1e85660
mcd-DEBUG: 06/16/2011 00:02:33.996208: mcd_manager_create_connection: Created a connection 0x1ec9250 for account: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.996244: _mcd_connection_connect: called for 0x1ec9250, account haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.996279: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.996318: _mcd_account_set_connection_status: haze/icq/_33456106010: 1 because 1
mcd-DEBUG: 06/16/2011 00:02:33.996352: mcd_account_freeze_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.996387: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 06/16/2011 00:02:33.996423: mcd_account_changed_property: called: Connection
mcd-DEBUG: 06/16/2011 00:02:33.996457: mcd_account_changed_property: First changed property
mcd-DEBUG: 06/16/2011 00:02:33.996942: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 06/16/2011 00:02:33.997030: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 06/16/2011 00:02:33.997095: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 06/16/2011 00:02:33.997165: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 06/16/2011 00:02:33.997236: mcd_account_thaw_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:33.997296: emit_property_changed: called
mcd-DEBUG: 06/16/2011 00:02:34.130794: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3345610601
mcd-DEBUG: 06/16/2011 00:02:34.131352: _mcd_connection_set_tp_connection: new connection is 0x1ed14f0
mcd-DEBUG: 06/16/2011 00:02:34.131397: mcd_account_changed_property: called: Connection
mcd-DEBUG: 06/16/2011 00:02:34.131434: mcd_account_changed_property: First changed property
mcd-DEBUG: 06/16/2011 00:02:34.133183: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 06/16/2011 00:02:34.134996: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3345610601: Early Get(Statuses) succeeded
mcd-DEBUG: 06/16/2011 00:02:34.135051: presence_get_statuses_cb: account haze/icq/_33456106010:
mcd-DEBUG: 06/16/2011 00:02:34.135090: presence_get_statuses_cb:   available
mcd-DEBUG: 06/16/2011 00:02:34.135128: presence_get_statuses_cb:   busy
mcd-DEBUG: 06/16/2011 00:02:34.135164: presence_get_statuses_cb:   offline
mcd-DEBUG: 06/16/2011 00:02:34.135200: presence_get_statuses_cb:   xa
mcd-DEBUG: 06/16/2011 00:02:34.135236: presence_get_statuses_cb:   away
mcd-DEBUG: 06/16/2011 00:02:34.135271: presence_get_statuses_cb:   hidden
mcd-DEBUG: 06/16/2011 00:02:34.135308: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 06/16/2011 00:02:34.135467: _mcd_dispatcher_add_connection: 0x1ec2830: 0x1ec9250 (/org/freedesktop/Telepathy/Connection/haze/icq/_3345610601)
mcd-DEBUG: 06/16/2011 00:02:34.135575: _mcd_connection_start_dispatching: 0x1ec9250
mcd-DEBUG: 06/16/2011 00:02:34.135724: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 06/16/2011 00:02:34.135792: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3345610601: Calling Connect()
mcd-DEBUG: 06/16/2011 00:02:34.140535: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 06/16/2011 00:02:34.140592: _mcd_account_set_connection_status: haze/icq/_33456106010: 1 because 1
mcd-DEBUG: 06/16/2011 00:02:34.140630: mcd_account_freeze_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:34.140667: mcd_account_changed_property: called: Connection
mcd-DEBUG: 06/16/2011 00:02:34.140703: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 06/16/2011 00:02:34.140738: emit_property_changed: called
mcd-DEBUG: 06/16/2011 00:02:34.140815: mcd_account_changed_property: First changed property
mcd-DEBUG: 06/16/2011 00:02:34.141045: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 06/16/2011 00:02:34.141096: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 06/16/2011 00:02:34.141132: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 06/16/2011 00:02:34.141175: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 06/16/2011 00:02:34.141213: mcd_account_thaw_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:34.141249: emit_property_changed: called
mcd-DEBUG: 06/16/2011 00:02:34.173065: connect_cb: called for connection 0x1ec9250
mcd-DEBUG: 06/16/2011 00:02:35.59312: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 06/16/2011 00:02:35.61758: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 06/16/2011 00:02:35.61875: _mcd_connection_release_tp_connection: 0x1ec9250
mcd-DEBUG: 06/16/2011 00:02:35.61958: _mcd_account_set_connection_status: haze/icq/_33456106010: 2 because 2
mcd-DEBUG: 06/16/2011 00:02:35.62020: mcd_account_freeze_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:35.62084: _mcd_account_set_connection_status: changing detailed D-Bus error from '' to 'org.freedesktop.Telepathy.Error.NetworkError'
mcd-DEBUG: 06/16/2011 00:02:35.62150: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 06/16/2011 00:02:35.62210: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 06/16/2011 00:02:35.62272: mcd_account_changed_property: called: Connection
mcd-DEBUG: 06/16/2011 00:02:35.62333: mcd_account_changed_property: First changed property
mcd-DEBUG: 06/16/2011 00:02:35.62649: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 06/16/2011 00:02:35.62728: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 06/16/2011 00:02:35.62793: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 06/16/2011 00:02:35.62932: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 06/16/2011 00:02:35.63003: mcd_account_thaw_properties: haze/icq/_33456106010
mcd-DEBUG: 06/16/2011 00:02:35.63066: emit_property_changed: called
mcd-DEBUG: 06/16/2011 00:02:35.63261: mcd_connection_invalidated_cb: Preparing for reconnection in 3 seconds
mcd-DEBUG: 06/16/2011 00:02:35.63334: on_connection_ready: got error: Network error


```

---

### Post by player999 on 2011-06-18
I've solved problem by installing and uninstalling Pidgin. It fixed my Empathy o_O

---

