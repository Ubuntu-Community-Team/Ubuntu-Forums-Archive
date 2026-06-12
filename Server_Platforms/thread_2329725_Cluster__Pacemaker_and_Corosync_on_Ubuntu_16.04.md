---
title: "Cluster : Pacemaker and Corosync on Ubuntu 16.04"
date: 2016-07-04
forum: Server Platforms
---

### Post by chris923 on 2016-07-04
Hello everybody :)

I've got a little question regarding my Pacemaker / Corosync cluster. I would like to run properly Pacemaker over Corosync but I always have the same problem and I cannot find a proper solution. 
Corosync is running well but the Pacemaker process always stops after 45 seconds.



Here is my log file with the errors. 




```

Jul 04 18:33:30 [662] bos3mep        cib:    error: xml_log:    Expecting an element nvpair, got nothing
Jul 04 18:33:30 [662] bos3mep        cib:    error: xml_log:    Expecting an element instance_attributes, got nothing
Jul 04 18:33:30 [662] bos3mep        cib:    error: xml_log:    Element nodes has extra content: node
Jul 04 18:33:30 [662] bos3mep        cib:    error: xml_log:    Invalid attribute update-origin for element cib
Jul 04 18:33:30 [663] bos3mep        cib:     info: crm_log_init:       Changed active directory to /var/lib/pacemaker/cores/hacluster
Jul 04 18:33:30 [663] bos3mep        cib:     info: get_cluster_type:   Verifying cluster type: 'corosync'
Jul 04 18:33:30 [663] bos3mep        cib:     info: get_cluster_type:   Assuming an active 'corosync' cluster
Jul 04 18:33:30 [663] bos3mep        cib:     info: validate_with_relaxng:      Creating RNG parser context
Jul 04 18:33:34 [723] bos3mep       lrmd:     info: crm_log_init:       Changed active directory to /var/lib/pacemaker/cores/root
Jul 04 18:33:34 [723] bos3mep       lrmd:     info: qb_ipcs_us_publish: server name: lrmd
Jul 04 18:33:34 [723] bos3mep       lrmd:    error: qb_ipcs_us_publish: Could not bind AF_UNIX (): Address already in use (98)
Jul 04 18:33:34 [723] bos3mep       lrmd:     info: qb_ipcs_us_withdraw:        withdrawing server sockets
Jul 04 18:33:34 [723] bos3mep       lrmd:    error: mainloop_add_ipc_server:    Could not start lrmd IPC server: Address already in use (-98)
Jul 04 18:33:34 [723] bos3mep       lrmd:     info: crm_xml_cleanup:    Cleaning up memory from libxml2
Jul 04 18:33:34 [619] bos3mep       crmd:   notice: crm_signal_dispatch:        Invoking handler for signal 15: Terminated
Jul 04 18:33:34 [619] bos3mep       crmd:  warning: do_log:     FSA: Input I_SHUTDOWN from crm_shutdown() received in state S_STARTING
Jul 04 18:33:34 [619] bos3mep       crmd:   notice: do_state_transition:        State transition S_STARTING -> S_STOPPING [ input=I_SHUTDOWN cause=C_SHUTDOWN origin=crm_shutdown ]
Jul 04 18:33:34 [619] bos3mep       crmd:     info: crm_cluster_disconnect:     Disconnecting from cluster infrastructure: corosync
Jul 04 18:33:34 [619] bos3mep       crmd:   notice: terminate_cs_connection:    Disconnecting from Corosync
Jul 04 18:33:34 [619] bos3mep       crmd:     info: cluster_disconnect_cpg:     No CPG connection
Jul 04 18:33:34 [619] bos3mep       crmd:     info: terminate_cs_connection:    No Quorum connection
Jul 04 18:33:34 [619] bos3mep       crmd:     info: crm_cluster_disconnect:     Disconnected from corosync
Jul 04 18:33:34 [619] bos3mep       crmd:     info: do_exit:    Performing A_EXIT_0 - gracefully exiting the CRMd
Jul 04 18:33:34 [619] bos3mep       crmd:     info: crm_xml_cleanup:    Cleaning up memory from libxml2
Jul 04 18:33:34 [618] bos3mep    pengine:   notice: crm_signal_dispatch:        Invoking handler for signal 15: Terminated
Jul 04 18:33:34 [618] bos3mep    pengine:     info: qb_ipcs_us_withdraw:        withdrawing server sockets
Jul 04 18:33:34 [618] bos3mep    pengine:     info: crm_xml_cleanup:    Cleaning up memory from libxml2
Jul 04 18:33:39 [615] bos3mep stonith-ng:     info: qb_ipcs_us_publish: server name: stonith-ng
Jul 04 18:33:39 [615] bos3mep stonith-ng:     info: pcmk_cpg_membership:        Node 1 joined group stonith-ng (counter=0.0)
Jul 04 18:33:39 [615] bos3mep stonith-ng:     info: pcmk_cpg_membership:        Node 1 still member of group stonith-ng (peer=bos3mep, counter=0.0)
Jul 04 18:33:43 [610] bos3mep pacemakerd:   notice: crm_signal_dispatch:        Invoking handler for signal 2: Interrupt
Jul 04 18:33:44 [610] bos3mep pacemakerd:   notice: crm_signal_dispatch:        Invoking handler for signal 2: Interrupt
Jul 04 18:33:44 [610] bos3mep pacemakerd:   notice: crm_signal_dispatch:        Invoking handler for signal 2: Interrupt
Jul 04 18:34:13 [616] bos3mep      attrd:     info: qb_ipcs_us_withdraw:        withdrawing server sockets
Jul 04 18:34:13 [616] bos3mep      attrd:     info: crm_xml_cleanup:    Cleaning up memory from libxml2





```


My environnement : 

Pacemaker 1.1.14 on Ubuntu 16.04 using corosync 2.3.5
Mon environnement : 


My configuration : 

The ssl keys have been shared between my 2 nodes.




my /etc/corosync/cosorync.conf file :


```

totem {
 version:                             2
 token:                               3000
 token_retransmits_before_loss_const: 10
 join:                                50
 vsftype:                             none
 max_messages:                        17
 clear_node_high_bit:                 yes
 rrp_mode:                            none
 secauth:                             off
 threads:                             32
 transport:                           udpu
 interface {
   member {
     memberaddr: 10.10.100.157
   }
   member {
     memberaddr: 10.10.100.158
   }
   ringnumber:  0
   bindnetaddr: 10.10.100.0
   mcastport:   5405
 }
}


logging {
 fileline:        off
 to_stderr:       yes
 to_logfile:      no
 to_syslog:       yes
 syslog_facility: daemon
 syslog_priority: info
 debug:           off
 timestamp:       on
 logger_subsys {
   subsys: AMF
   debug:  off
   tags:   enter|leave|trace1|trace2|trace3|trace4|trace6
 }
}


amf {
 mode: disabled
}


aisexec {
 user:  root
 group: root
}


quorum {
 provider: corosync_votequorum
 two_node: 1
}


nodelist {
 node {
   ring0_addr: 10.10.100.157
  nodeid: 1
 }
 node {
   ring0_addr: 10.10.100.158
   nodeid: 2
 }
}





```


Best regards

Chris.

---

