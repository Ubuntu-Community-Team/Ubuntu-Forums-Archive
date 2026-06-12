---
title: "Ansible errors with incorrect sudo password"
date: 2019-12-02
forum: Security
---

### Post by TechnoJunky on 2019-12-02
This was previously working, but about a month ago, after an update, it stopped.  This is for my home network.  I have 3 Kubuntu computers, 1 working as a server, with Ansible installed, 2 client workstations.   

I can log into all 3 computers with the same ID and same password.  Once there I can run 'sudo apt-get update (or upgrade), on all 3.
I setup passwordless SSH keys on each of computers.  I can ssh into the server and then ssh into each of the clients from the server.
On the server, in my home directory, I have a folder called playbooks.  In it I have 3 files.  1 - update.yml, 2 - update.sh, 3 - secret.  

When I run 'ansible-vault edit secret', I can see 'ansible_sudo_pass: xxxxxxx' (xxxxxx replaces my real password).

update.sh contains only 1 line, 'ansible-playbook update.yml  --ask-vault-pass'  When I run this, it asks for the vault password, then shows the task names where it errors out.

update.yml contains the following lines:
---

 - name: Update Apps
   hosts: kubuntu

   vars_files:
     - secret

   tasks:
   - name: Update Cache
     become: true
     apt: 
       force_apt_get: yes
       update_cache: yes

   - name: Apt-get dist-upgrade  
     become: true
     apt:
       force_apt_get: yes
       upgrade: dist
       autoclean: yes
       autoremove: yes

Like I said, this used to work, now I get the sudo password error.   Can someone help me figure this out?

---

### Post by kevdog on 2019-12-03
I'm going to say I am not an ansible expert, so I'm not sure what is causing your problem. 

I can only tell you the way I'm setting things up which works for me -- and I'm sure there are other ways of doing things

I tend to use an inventory file for my playbooks using the xml, rather than ini format.  I chose to use the xml format since it's consistent with the same format needed within the playbook file.

On the command line I call my playbook with the inventory file and vault-password-file like this with vars.yml=playbook file and hostname.yml=inventory file

ansible-playbook vars.yml -i <hostname.yml> --vault-password-file <vault-password-file>

Within my inventory file I have a structure that looks like the following:

```

all:
  hosts:
  vars:
    root_password: !vault |
                   $ANSIBLE_VAULT;1.1;AES256
                   alakfjalkfjal;kfja--A_BUNCH_OF_LETTERS_AND_NUMBERS_OF_THE_ENCRYPTED_ROOT_PASSWORD--afadafjdfjd
                   kaakakladkasdkdadfkasdljafjkadfjkfdjkfadjkfdjkdaffjkdasadfl;knvndapon
                   adnapofnvpnoapnoeponeweqwpid098ad9daqwen20qwe0ads90cvnadvsnopfdaopdfn
                   a0adsoidafopn
    ansible_become: yes
    ansible_become_password: "{{ root_password }}"
    root_user: root

    # IP address or hostname of web accessible server where the fullchain.pem file is located
    remote_ip_address: "10.0.1.158"
    
    # If modifying remote_path please be sure not to add / before or after path since call to remote server
    # will be transformed to https://<remote_ip_address>/<remote_path>/
    remote_path: "certs"

    # Call to remote server will be https://<remote_ip_address>/<remote_path>/<fullchain_pem_file>
    fullchain_pem_file: "fullchain.pem"
    # Call to remote server will be https://<remote_ip_address>/<remote_path>/<fullchain_pem_hash_file>
    fullchain_pem_hash_file: "{{ fullchain_pem_file }}.sha256"

    # The following is directory on the server that is read/writeable by the ansible script user
    # This can be modified to any temporary directory as all files placed into this directory will be
    # removed at the end of the script
    local_temp_directory: "/var/tmp"


  # local_certificate_directoy refers to directory where the certs will be placed and utilized
  # some examples may be /etc/letsencrypt/<domain name>/live
  #                      /usr/local/etc/letsencrypt/<domain name>/live
  children:
    linux:
      hosts:
        10.0.1.100:
      vars:
        local_certificate_directory: /etc/letsencrypt/<domain name>/live
        root_group: root
    bsd:
      hosts:
        192.168.1.6:
      vars:
        local_certificate_directory: /usr/local/etc/letsencrypt<domain name>/live
        root_group: wheel

```

I'm not sure if this helps you or not.  I'm certain you could probably not use the inventory file and include the variable at the top of your playbook if needed.  
Here's a link to my github which may or may not be of help to you:
[https://github.com/kevdogg/ansible_push_fullchain.pem/blob/master/hostname-example.yml](https://github.com/kevdogg/ansible_push_fullchain.pem/blob/master/hostname-example.yml)

---

### Post by TechnoJunky on 2019-12-03
I use a hosts file, and reference it in the line "hosts: kubuntu".  Mine is stored in the default /etc/ansible/hosts file.  This doesn't appear to be the issue.  When I run the script, it lists all 3 computers, and shows each failed with the sudo password error I mentioned in the subject.  

I realize I failed to post the actutal wording though, so this is the error message "fatal: [desktop1]: FAILED! => {"msg": "Incorrect sudo password"}"

Thanks for responding though.

---

### Post by kevdog on 2019-12-04
You havent exactly given a lot of detail to work with.  I'm not sure.  Make sure you can manually ssh into each box and perform a su operation.  I'm not sure if ansible become uses su or sudo to become root.  There is a difference believe it or not between the two commands, so I'd check both commands. Maybe try recreating the vault password file if everything works.  For what its worth, I'm not having any issues with using ansible and becoming root, so I'd guess it might be a simple change introduced through an update on the systems.

---

