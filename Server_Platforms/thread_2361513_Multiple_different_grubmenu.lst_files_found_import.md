---
title: "Multiple different grub/menu.lst files found importing OVA to AWS EC2"
date: 2017-05-17
forum: Server Platforms
---

### Post by alex-corretge on 2017-05-17
[COLOR=#242729][FONT=Arial]Trying to import[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][https://cloud-images.ubuntu.com/releases/16.04/release/ubuntu-16.04-server-cloudimg-amd64.ova](https://cloud-images.ubuntu.com/releases/16.04/release/ubuntu-16.04-server-cloudimg-amd64.ova)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]to Amazon EC2 with
[/FONT][/COLOR]
aws ec2 import-image 
    --description "XXX" 
    --disk-containers file://xxxx.json 
    --platform Linux 
    --profile XXX
[COLOR=#242729][FONT=Arial]
I get StatusMessage: ClientError: Multiple different grub/menu.lst files found.[/FONT][/COLOR]

{
    "ImportImageTasks": [
        {
            "Status": "deleted",
            "Description": "XXXX",
            "Platform": "Linux",
            "SnapshotDetails": [
                {
                    "UserBucket": {
                        "S3Bucket": "images.XXXX",
                        "S3Key": "ubuntu-16.04-server-cloudimg-amd64.ova"
                    },
                    "DiskImageSize": 320673792.0,
                    "Format": "VMDK"
                }
            ],
            "StatusMessage": "ClientError: Multiple different grub/menu.lst files found.",
            "ImportTaskId": "import-ami-XXXX"
        }
    ]
}
[COLOR=#242729][FONT=Arial]
Is it possible to import official Ubuntu 16.04 LTS OVA into AWS EC2?

[/FONT][/COLOR]

---

### Post by Habitual on 2017-05-17
They have a few up there already, [https://cloud-images.ubuntu.com/locator/ec2/](https://cloud-images.ubuntu.com/locator/ec2/)

or 
[https://rzn.id.au/tech/converting-an-ova-to-an-amazon-ami/](https://rzn.id.au/tech/converting-an-ova-to-an-amazon-ami/)

---

