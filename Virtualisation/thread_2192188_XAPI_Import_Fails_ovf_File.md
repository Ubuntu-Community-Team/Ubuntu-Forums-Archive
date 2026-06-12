---
title: "XAPI Import Fails ovf File"
date: 2013-12-06
forum: Virtualisation
---

### Post by thilo.mendorf on 2013-12-06
Hi,
i set up a XEN XAPI Server . (on ubuntu)
Now i like to import a ovf File with the xencenter which has been created by the XenConverter.
But XenCenter allways tells me that the import Fails...
Thats all...

Here i paste the xapi Log file. But did not found the error :-(

Any ideas?

[20131206T15:47:10.073Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:e6316ae9c924|backgroundscheduler] Removing function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 from queue
[20131206T15:47:10.126Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e6316ae9c924|xapi_event] last_generation=10941 cur_id=11227
[20131206T15:47:10.126Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e6316ae9c924|xapi_event] ctime: 11218 mtime:11219 dtime:0 objref:OpaqueRef:98ed50ed-07dd-444a-b5db-ca751c3a6e8b
[20131206T15:47:10.223Z|debug|lxserv01|152 INET 127.0.0.1:80|VM.create R:965c89897d6e|audit] VM.create: name_label = 'pc18' name_description = 'AT/AT COMPATIBLE'
[20131206T15:47:10.234Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e8566cab870b|xapi_event] last_generation=11219 cur_id=0
[20131206T15:47:10.234Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e8566cab870b|xapi_event] ctime: 11230 mtime:11230 dtime:0 objref:OpaqueRef:965c8989-7d6e-8a0f-56cb-c6201eadb57f
[20131206T15:47:10.234Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e8566cab870b|xapi_event] last_generation=11219 cur_id=0
[20131206T15:47:10.234Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e8566cab870b|xapi_event] ctime: 11216 mtime:0 dtime:11227 objref:OpaqueRef:75ba90d3-86cc-a01e-a894-169f399d8e79
[20131206T15:47:10.293Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:6a4a0980886a|xapi_event] last_generation=11230 cur_id=0
[20131206T15:47:10.299Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:6a4a0980886a|xapi_event] ctime: 11230 mtime:11242 dtime:0 objref:OpaqueRef:965c8989-7d6e-8a0f-56cb-c6201eadb57f
[20131206T15:47:10.299Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:6a4a0980886a|xapi_event] last_generation=11230 cur_id=0
[20131206T15:47:10.299Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:6a4a0980886a|xapi_event] ctime: 11234 mtime:11239 dtime:0 objref:OpaqueRef:c86aa3b8-62c8-fa92-5cc1-02241f4448c3
[20131206T15:47:10.300Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:6a4a0980886a|xapi_event] last_generation=11230 cur_id=0
[20131206T15:47:10.300Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:6a4a0980886a|xapi_event] ctime: 11233 mtime:11233 dtime:0 objref:OpaqueRef:ea451ba1-94eb-b482-2ea1-d1e03e29563f
[20131206T15:47:10.434Z| info|lxserv01|152 INET 127.0.0.1:80|dispatch:VM.add_to_other_config D:5608711753d8|api_effect] VM.add_to_other_config
[20131206T15:47:10.448Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e6d92550967c|xapi_event] last_generation=11242 cur_id=0
[20131206T15:47:10.450Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e6d92550967c|xapi_event] ctime: 11230 mtime:0 dtime:11247 objref:OpaqueRef:965c8989-7d6e-8a0f-56cb-c6201eadb57f
[20131206T15:47:10.450Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e6d92550967c|xapi_event] last_generation=11242 cur_id=0
[20131206T15:47:10.450Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:e6d92550967c|xapi_event] ctime: 11234 mtime:11251 dtime:0 objref:OpaqueRef:c86aa3b8-62c8-fa92-5cc1-02241f4448c3
[20131206T15:47:10.509Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|backgroundscheduler] Adding function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 to queue, start=30.499925, type=OneShot
[20131206T15:47:10.510Z|debug|lxserv01|19|Starting periodic scheduler D:e8359bbd67be|backgroundscheduler] Sleeping until next event (30.500880 seconds)
[20131206T15:47:10.611Z|debug|lxserv01|152 INET 127.0.0.1:80|VM.set_appliance R:27018ca9bd9f|audit] VM.set_appliance: self = '7b4d5c0e-181e-d2fb-8702-70d5896092bb (pc18)'; value = '5ca1aeaf-6616-6dd8-1fd0-8acfb24a4a5e (pc18)';
[20131206T15:47:10.613Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|backgroundscheduler] Removing function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 from queue
[20131206T15:47:10.664Z|debug|lxserv01|448 INET 127.0.0.1:80|Connection to VM console R:7a9da8dc5f9b|console] VM OpaqueRef:8d0c749f-c4b7-3b52-e2c4-cb74a72c9bd5 console port: None
[20131206T15:47:10.666Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|xapi_event] last_generation=11251 cur_id=11268
[20131206T15:47:10.667Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|xapi_event] ctime: 11263 mtime:11263 dtime:0 objref:OpaqueRef:7a9da8dc-5f9b-ce79-e988-19fbc0c26703
[20131206T15:47:10.668Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|xapi_event] last_generation=11251 cur_id=11268
[20131206T15:47:10.668Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|xapi_event] ctime: 11234 mtime:11261 dtime:0 objref:OpaqueRef:c86aa3b8-62c8-fa92-5cc1-02241f4448c3
[20131206T15:47:10.668Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|xapi_event] last_generation=11251 cur_id=11268
[20131206T15:47:10.668Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:2d4742de683a|xapi_event] ctime: 11218 mtime:11262 dtime:0 objref:OpaqueRef:98ed50ed-07dd-444a-b5db-ca751c3a6e8b
[20131206T15:47:10.713Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:01f433593a8d|xapi_event] last_generation=11263 cur_id=0
[20131206T15:47:10.713Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:01f433593a8d|xapi_event] ctime: 11263 mtime:0 dtime:11274 objref:OpaqueRef:7a9da8dc-5f9b-ce79-e988-19fbc0c26703
[20131206T15:47:10.713Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:01f433593a8d|xapi_event] last_generation=11263 cur_id=0
[20131206T15:47:10.713Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:01f433593a8d|xapi_event] ctime: 11257 mtime:0 dtime:11268 objref:OpaqueRef:27018ca9-bd9f-8139-923c-fb1d3b408c85
[20131206T15:47:10.771Z|debug|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|backgroundscheduler] Adding function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 to queue, start=30.499804, type=OneShot
[20131206T15:47:10.771Z|debug|lxserv01|19|Starting periodic scheduler D:e8359bbd67be|backgroundscheduler] Sleeping until next event (30.500761 seconds)
[20131206T15:47:11.085Z|debug|lxserv01|150 INET 127.0.0.1:80|VM.get_allowed_VBD_devices D:bfb37a025993|audit] VM.get_allowed_VBD_devices: VM = '7b4d5c0e-181e-d2fb-8702-70d5896092bb (pc18)'
[20131206T15:47:11.094Z|debug|lxserv01|150 INET 127.0.0.1:80|VBD.create R:d67e8128b021|audit] VBD.create: VM = '7b4d5c0e-181e-d2fb-8702-70d5896092bb (pc18)'; VDI = 'invalid'
[20131206T15:47:11.096Z|debug|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|backgroundscheduler] Removing function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 from queue
[20131206T15:47:11.101Z|debug|lxserv01|150 INET 127.0.0.1:80|VBD.create R:d67e8128b021|xapi] VBD.create (device = 2; uuid = 3d0cb71d-4d46-229c-0374-d73628962893; ref = OpaqueRef:0ca1b9d7-9597-8876-d484-7384591fab08)
[20131206T15:47:11.154Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|xapi_event] last_generation=11274 cur_id=11296
[20131206T15:47:11.154Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|xapi_event] ctime: 11234 mtime:11287 dtime:0 objref:OpaqueRef:c86aa3b8-62c8-fa92-5cc1-02241f4448c3
[20131206T15:47:11.154Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|xapi_event] last_generation=11274 cur_id=11296
[20131206T15:47:11.154Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|xapi_event] ctime: 11287 mtime:11289 dtime:0 objref:OpaqueRef:0ca1b9d7-9597-8876-d484-7384591fab08
[20131206T15:47:11.154Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|xapi_event] last_generation=11274 cur_id=11296
[20131206T15:47:11.154Z| info|lxserv01|152 INET 127.0.0.1:80|event.from D:000256d1f6ab|xapi_event] ctime: 11286 mtime:11286 dtime:0 objref:OpaqueRef:b2fab4ee-c17c-e9e1-2fc2-45eb86acc8b1
[20131206T15:47:11.325Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:f080fb2820a9|xapi_event] last_generation=11289 cur_id=0
[20131206T15:47:11.325Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:f080fb2820a9|xapi_event] ctime: 11284 mtime:0 dtime:11296 objref:OpaqueRef:d67e8128-b021-ece0-b1e6-b6d1d01422a6
[20131206T15:47:11.376Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:01f3758ec16b|backgroundscheduler] Adding function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 to queue, start=30.499925, type=OneShot
[20131206T15:47:11.376Z|debug|lxserv01|19|Starting periodic scheduler D:e8359bbd67be|backgroundscheduler] Sleeping until next event (30.500883 seconds)
[20131206T15:47:12.071Z|debug|lxserv01|152 INET 127.0.0.1:80|VDI.create R:fba4807e4748|audit] VDI.create: SR = '377d1f1a-5877-3a56-1777-3c94fa4c07b4 (xen01)'; name label = 'Hard Disk Image'
[20131206T15:47:12.072Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:01f3758ec16b|backgroundscheduler] Removing function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 from queue
[20131206T15:47:12.078Z|debug|lxserv01|152 INET 127.0.0.1:80|VDI.create R:fba4807e4748|xapi] Marking SR for VDI.create (task=OpaqueRef:fba4807e-4748-3830-2849-82571a407162)
[20131206T15:47:12.089Z| info|lxserv01|152 INET 127.0.0.1:80|VDI.create R:fba4807e4748|storage_impl] VDI.create task:OpaqueRef:fba4807e-4748-3830-2849-82571a407162 sr:377d1f1a-5877-3a56-1777-3c94fa4c07b4 vdi_info:{"vdi": "", "name_label": "Hard Disk Image", "name_description": "SCSI BUS[0] LUN[0] PORT[3] TARGETID[0]", "ty": "user", "metadata_of_pool": "", "is_a_snapshot": false, "snapshot_time": "19700101T00:00:00Z", "snapshot_of": "", "read_only": false, "virtual_size": 25778192384, "physical_utilisation": 0} params:
[20131206T15:47:12.101Z|debug|lxserv01|152 INET 127.0.0.1:80|VDI.create R:fba4807e4748|dummytaskhelper] task VDI.create D:b9a7597cdada created by task R:fba4807e4748
[20131206T15:47:12.104Z|debug|lxserv01|152 INET 127.0.0.1:80|VDI.create D:b9a7597cdada|sm] SM ext vdi_create sr=OpaqueRef:17b47bee-6744-16bc-1b6a-bee55d55ddaf sm_config=[] type=[user] size=25778192384
[20131206T15:47:12.105Z| info|lxserv01|152 INET 127.0.0.1:80|sm_exec D:c6b235486207|xapi] Session.create trackid=9be672f1a72fb158013dce44c1df30fc pool=false uname= is_local_superuser=true auth_user_sid= parent=trackid=9834f5af41c964e225f24279aefe4e49
[20131206T15:47:12.112Z|debug|lxserv01|152 INET 127.0.0.1:80|sm_exec D:c6b235486207|xapi] Attempting to open /var/lib/xcp/xapi
[20131206T15:47:12.115Z|debug|lxserv01|449 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:session.get_uuid D:98f0edf3ec72 created by task D:c6b235486207
[20131206T15:47:12.122Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:01f3758ec16b|xapi_event] last_generation=11296 cur_id=11315
[20131206T15:47:12.123Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:01f3758ec16b|xapi_event] ctime: 11309 mtime:11310 dtime:0 objref:OpaqueRef:fba4807e-4748-3830-2849-82571a407162
[20131206T15:47:12.123Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:01f3758ec16b|xapi_event] last_generation=11296 cur_id=11315
[20131206T15:47:12.123Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:01f3758ec16b|xapi_event] ctime: 6362 mtime:11314 dtime:0 objref:OpaqueRef:17b47bee-6744-16bc-1b6a-bee55d55ddaf
[20131206T15:47:12.276Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:7b4795d415eb|backgroundscheduler] Adding function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 to queue, start=30.499927, type=OneShot
[20131206T15:47:12.277Z|debug|lxserv01|19|Starting periodic scheduler D:e8359bbd67be|backgroundscheduler] Sleeping until next event (30.500884 seconds)
[20131206T15:47:12.304Z|debug|lxserv01|450 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:host.get_other_config D:0a2c6366f478 created by task D:b9a7597cdada
[20131206T15:47:12.307Z|debug|lxserv01|450 UNIX /var/lib/xcp/xapi||http_critical] Premature termination of connection!
[20131206T15:47:12.356Z|debug|lxserv01|451 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:VDI.db_introduce D:5d0249e7af3a created by task D:b9a7597cdada
[20131206T15:47:12.359Z| info|lxserv01|451 UNIX /var/lib/xcp/xapi|dispatch:VDI.db_introduce D:5d0249e7af3a|taskhelper] task VDI.db_introduce R:ac3305724606 (uuid:e0702ae5-9b64-c147-bb22-de05c3363492) created (trackid=9be672f1a72fb158013dce44c1df30fc) by task D:b9a7597cdada
[20131206T15:47:12.361Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:7b4795d415eb|backgroundscheduler] Removing function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 from queue
[20131206T15:47:12.366Z|debug|lxserv01|451 UNIX /var/lib/xcp/xapi|VDI.db_introduce R:ac3305724606|xapi] {pool,db}_introduce uuid=c8c4a9bc-7a0a-4668-a58e-4cd8ac7fc6ca name_label=Hard Disk Image
[20131206T15:47:12.368Z|debug|lxserv01|451 UNIX /var/lib/xcp/xapi|VDI.db_introduce R:ac3305724606|xapi] VDI.introduce read_only = false
[20131206T15:47:12.411Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7b4795d415eb|xapi_event] last_generation=11314 cur_id=11333
[20131206T15:47:12.418Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7b4795d415eb|xapi_event] ctime: 6362 mtime:11324 dtime:0 objref:OpaqueRef:17b47bee-6744-16bc-1b6a-bee55d55ddaf
[20131206T15:47:12.418Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7b4795d415eb|xapi_event] last_generation=11314 cur_id=11333
[20131206T15:47:12.418Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7b4795d415eb|xapi_event] ctime: 11324 mtime:11325 dtime:0 objref:OpaqueRef:4e3fe06f-8ce1-3df2-e9be-93fb6fabcba7
[20131206T15:47:12.425Z|debug|lxserv01|451 UNIX /var/lib/xcp/xapi||http_critical] Premature termination of connection!
[20131206T15:47:12.435Z|debug|lxserv01|452 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:SR.get_virtual_allocation D:1e414cb310ee created by task D:b9a7597cdada
[20131206T15:47:12.443Z|debug|lxserv01|452 UNIX /var/lib/xcp/xapi||http_critical] Premature termination of connection!
[20131206T15:47:12.444Z|debug|lxserv01|453 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:SR.get_by_uuid D:82451ff0613b created by task D:b9a7597cdada
[20131206T15:47:12.450Z|debug|lxserv01|453 UNIX /var/lib/xcp/xapi||http_critical] Premature termination of connection!
[20131206T15:47:12.450Z|debug|lxserv01|454 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:SR.set_virtual_allocation D:c728f6f90705 created by task D:b9a7597cdada
[20131206T15:47:12.468Z|debug|lxserv01|454 UNIX /var/lib/xcp/xapi||http_critical] Premature termination of connection!
[20131206T15:47:12.469Z|debug|lxserv01|455 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:SR.set_physical_size D:c3f69f7d535b created by task D:b9a7597cdada
[20131206T15:47:12.486Z|debug|lxserv01|455 UNIX /var/lib/xcp/xapi||http_critical] Premature termination of connection!
[20131206T15:47:12.490Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c15e9de96c96|xapi_event] last_generation=11325 cur_id=0
[20131206T15:47:12.496Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c15e9de96c96|xapi_event] ctime: 11322 mtime:0 dtime:11333 objref:OpaqueRef:ac330572-4606-b29a-5d5d-8d2fa6274cf0
[20131206T15:47:12.496Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c15e9de96c96|xapi_event] last_generation=11325 cur_id=0
[20131206T15:47:12.496Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c15e9de96c96|xapi_event] ctime: 6362 mtime:11342 dtime:0 objref:OpaqueRef:17b47bee-6744-16bc-1b6a-bee55d55ddaf
[20131206T15:47:12.499Z|debug|lxserv01|456 UNIX /var/lib/xcp/xapi||dummytaskhelper] task dispatch:SR.set_physical_utilisation D:553c0a25aa50 created by task D:b9a7597cdada
[20131206T15:47:12.519Z|debug|lxserv01|456 UNIX /var/lib/xcp/xapi||http_critical] Premature termination of connection!
[20131206T15:47:12.545Z| info|lxserv01|152 INET 127.0.0.1:80|sm_exec D:c6b235486207|xapi] Session.destroy trackid=9be672f1a72fb158013dce44c1df30fc
[20131206T15:47:12.546Z|debug|lxserv01|152 INET 127.0.0.1:80|VDI.create R:fba4807e4748|xapi] OpaqueRef:4e3fe06f-8ce1-3df2-e9be-93fb6fabcba7 snapshot_of <- OpaqueRef:NULL
[20131206T15:47:12.547Z|debug|lxserv01|152 INET 127.0.0.1:80|VDI.create R:fba4807e4748|xapi] Unmarking SR after VDI.create (task=OpaqueRef:fba4807e-4748-3830-2849-82571a407162)
[20131206T15:47:12.673Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c0833155022a|xapi_event] last_generation=11342 cur_id=0
[20131206T15:47:12.674Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c0833155022a|xapi_event] ctime: 11309 mtime:0 dtime:11358 objref:OpaqueRef:fba4807e-4748-3830-2849-82571a407162
[20131206T15:47:12.674Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c0833155022a|xapi_event] last_generation=11342 cur_id=0
[20131206T15:47:12.674Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c0833155022a|xapi_event] ctime: 6362 mtime:11351 dtime:0 objref:OpaqueRef:17b47bee-6744-16bc-1b6a-bee55d55ddaf
[20131206T15:47:12.674Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c0833155022a|xapi_event] last_generation=11342 cur_id=0
[20131206T15:47:12.674Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:c0833155022a|xapi_event] ctime: 11324 mtime:11349 dtime:0 objref:OpaqueRef:4e3fe06f-8ce1-3df2-e9be-93fb6fabcba7
[20131206T15:47:12.798Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|backgroundscheduler] Adding function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 to queue, start=30.499925, type=OneShot
[20131206T15:47:12.801Z|debug|lxserv01|19|Starting periodic scheduler D:e8359bbd67be|backgroundscheduler] Sleeping until next event (30.500867 seconds)
[20131206T15:47:12.883Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|audit] Host.call_plugin host = '1a2b0f85-d46c-3d35-4b06-92d69b84a699 (lxserv01)'; plugin = 'transfer'; fn = 'expose'; args = [ read_only: false; vdi_uuid: c8c4a9bc-7a0a-4668-a58e-4cd8ac7fc6ca; transfer_mode: ISCSI; network_mode: dhcp; network_uuid: 97f4e009-ef2a-e175-5f39-4737a4e3354b ]
[20131206T15:47:12.883Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|backgroundscheduler] Removing function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 from queue
[20131206T15:47:12.890Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|backtrace] Raised at xapi_plugins.ml:26.13-82 -> xapi_plugins.ml:31.20-43 -> message_forwarding.ml:233.25-44 -> rbac.ml:229.16-23
[20131206T15:47:12.891Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|backtrace] Raised at rbac.ml:238.10-15 -> server_helpers.ml:79.11-41
[20131206T15:47:12.891Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|dispatcher] Server_helpers.exec exception_handler: Got exception XENAPI_MISSING_PLUGIN: [ transfer ]
[20131206T15:47:12.891Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|dispatcher] Raised at string.ml:150.25-34 -> stringext.ml:108.13-29
[20131206T15:47:12.891Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|backtrace] Raised at string.ml:150.25-34 -> stringext.ml:108.13-29
[20131206T15:47:12.914Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|xapi] Raised at server_helpers.ml:94.14-15 -> pervasiveext.ml:22.2-9
[20131206T15:47:12.916Z|debug|lxserv01|152 INET 127.0.0.1:80|host.call_plugin R:9f897749b8bb|xapi] Raised at pervasiveext.ml:26.22-25 -> pervasiveext.ml:22.2-9
[20131206T15:47:12.926Z|debug|lxserv01|152 INET 127.0.0.1:80|dispatch:host.call_plugin D:5f945a45130c|xapi] Raised at pervasiveext.ml:26.22-25 -> pervasiveext.ml:22.2-9
[20131206T15:47:12.936Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|backgroundscheduler] Adding function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 to queue, start=30.362612, type=OneShot
[20131206T15:47:12.936Z|debug|lxserv01|19|Starting periodic scheduler D:e8359bbd67be|backgroundscheduler] Sleeping until next event (30.363557 seconds)
[20131206T15:47:12.936Z|debug|lxserv01|152 INET 127.0.0.1:80|dispatch:host.call_plugin D:5f945a45130c|backtrace] Raised at pervasiveext.ml:26.22-25 -> server_helpers.ml:153.10-106 -> server.ml:15458.19-182 -> server_helpers.ml:119.4-7
[20131206T15:47:13.290Z|debug|lxserv01|152 INET 127.0.0.1:80|VM.destroy R:3e4d7935eedf|audit] VM.destroy: VM = '7b4d5c0e-181e-d2fb-8702-70d5896092bb (pc18)'
[20131206T15:47:13.293Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|backgroundscheduler] Removing function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 from queue
[20131206T15:47:13.316Z|debug|lxserv01|152 INET 127.0.0.1:80|VM.destroy R:3e4d7935eedf|xapi] VM.destroy: deleting DB records
[20131206T15:47:13.344Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] last_generation=11358 cur_id=11389
[20131206T15:47:13.344Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] ctime: 11379 mtime:11380 dtime:0 objref:OpaqueRef:3e4d7935-eedf-73a5-b9c1-e9ab5f6591c9
[20131206T15:47:13.345Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] last_generation=11358 cur_id=11389
[20131206T15:47:13.345Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] ctime: 11234 mtime:11387 dtime:0 objref:OpaqueRef:c86aa3b8-62c8-fa92-5cc1-02241f4448c3
[20131206T15:47:13.345Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] last_generation=11358 cur_id=11389
[20131206T15:47:13.345Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] ctime: 11218 mtime:11388 dtime:0 objref:OpaqueRef:98ed50ed-07dd-444a-b5db-ca751c3a6e8b
[20131206T15:47:13.345Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] last_generation=11358 cur_id=11389
[20131206T15:47:13.345Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:7a5a5d9b5e53|xapi_event] ctime: 11286 mtime:0 dtime:11389 objref:OpaqueRef:b2fab4ee-c17c-e9e1-2fc2-45eb86acc8b1
[20131206T15:47:13.357Z|debug|lxserv01|152 INET 127.0.0.1:80|VM.destroy R:3e4d7935eedf|xapi] Raised at db_cache_types.ml:104.27-69 -> db_cache_impl.ml:147.11-44 -> pervasiveext.ml:22.2-9
[20131206T15:47:13.369Z|debug|lxserv01|152 INET 127.0.0.1:80|VM.destroy R:3e4d7935eedf|xapi] Raised at db_cache_types.ml:104.27-69 -> db_cache_impl.ml:232.11-44 -> pervasiveext.ml:22.2-9
[20131206T15:47:13.529Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] last_generation=11389 cur_id=0
[20131206T15:47:13.529Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] ctime: 11379 mtime:0 dtime:11399 objref:OpaqueRef:3e4d7935-eedf-73a5-b9c1-e9ab5f6591c9
[20131206T15:47:13.529Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] last_generation=11389 cur_id=0
[20131206T15:47:13.529Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] ctime: 11234 mtime:0 dtime:11393 objref:OpaqueRef:c86aa3b8-62c8-fa92-5cc1-02241f4448c3
[20131206T15:47:13.530Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] last_generation=11389 cur_id=0
[20131206T15:47:13.530Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] ctime: 11233 mtime:0 dtime:11392 objref:OpaqueRef:ea451ba1-94eb-b482-2ea1-d1e03e29563f
[20131206T15:47:13.530Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] last_generation=11389 cur_id=0
[20131206T15:47:13.530Z| info|lxserv01|150 INET 127.0.0.1:80|event.from D:60ad5455bf49|xapi_event] ctime: 11287 mtime:0 dtime:11391 objref:OpaqueRef:0ca1b9d7-9597-8876-d484-7384591fab08
[20131206T15:47:13.698Z|debug|lxserv01|150 INET 127.0.0.1:80|event.from D:cde6d763afcd|backgroundscheduler] Adding function event_from_timeout_OpaqueRef:68b5608f-454f-f8ce-06fb-a5e14726ba29 to queue, start=30.499927, type=OneShot
[20131206T15:47:13.699Z|debug|lxserv01|19|Starting periodic scheduler D:e8359bbd67be|backgroundscheduler] Sleeping until next event (30.500882 seconds)
^C

---

