---
title: "Openstack on LXD and Juju issue"
date: 2018-06-14
forum: Ubuntu Cloud and Juju
---

### Post by quartzeye on 2018-06-14
So I have a large 18.04 VM running and have successfully configured LXD.  I followed the instructions on the Openstack-on-LXD page to get a stack running using Juju.  All is good.  I also did this using conjure-up but the deployment with conjure-up did not include Heat.

Now comes my issue.  Openstack-on-LXD creates compute nodes with QEMU as the default virt-type while conjure-up uses LXD.  In both installs, I want to create (2) host aggregates and availability zones, place (1) compute node in each host aggregate, then set the virt-type on one to KVM and the other as LXD.  Neither install method seems to allow me to do this and neither deployed environment seems to allow me to manage this post install.

Primarily, with Juju, when I go to the Juju GUI I can not configure each compute node independent of each other.  I can create the AZ's and HA's in the Horizon dashboard but when I go to the compute container, the nova.conf tells me it is manages by Juju and any edits will be overwritten.

So, I am guessing that I can edit the [COLOR="#0000FF"]"bundle-bionic-queens.yaml"[/COLOR] file and add the virt-type option to the nove-compute section as follows:

  nova-compute:
    annotations:
      gui-x: '250'
      gui-y: '250'
    charm: cs:nova-compute
    [COLOR="#0000FF"]num_units: 2[/COLOR]
    options:
      enable-live-migration: False
      enable-resize: False
      migration-auth-type: ssh
      openstack-origin: cloud: xenial-queens
      force-raw-images: False
      [COLOR="#0000FF"]virt-type: kvm
[/COLOR]
But can I create (2) compute nodes by adding in a second nova-compute stanza like this:

  nova-compute:
    annotations:
      gui-x: '250'
      gui-y: '250'
    charm: cs:nova-compute
    [COLOR="#0000FF"]num_units: 1[/COLOR]
    options:
      enable-live-migration: False
      enable-resize: False
      migration-auth-type: ssh
      openstack-origin: cloud: xenial-queens
      force-raw-images: False
      [COLOR="#0000FF"]virt-type: kvm[/COLOR]
      [COLOR="#0000FF"]default-availability-zone: azKVM[/COLOR]
  nova-compute:
    annotations:
      gui-x: '250'
      gui-y: '250'
    charm: cs:nova-compute
    [COLOR="#0000FF"]num_units: 1[/COLOR]
    options:
      enable-live-migration: False
      enable-resize: False
      migration-auth-type: ssh
      openstack-origin: cloud: xenial-queens
      force-raw-images: False
      [COLOR="#0000FF"]virt-type: lxd[/COLOR]
      [COLOR="#0000FF"]default-availability-zone: azLXD[/COLOR]

Also, in the charm it says [COLOR="#0000FF"]"NOTE: Availability zones must be created manually using the 'openstack aggregate create' command."[/COLOR]  That seems to be an issue as I have to have openstack installed first and cannot have them created in one of the other charms at install.  I don't see how I can I run a base install with (1) compute node, create the AZ's then add the second compute node in the Juju GUI then set the virt-type and AZ at that time for the second compute node as JuJu doesn't let me set the properties for each compute-node.

I am confident that what I am trying to do is possible but I cannot seem to find any info to get me to the next step.  Any help would be appreciated.

---

