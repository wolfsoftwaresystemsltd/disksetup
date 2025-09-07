# disksetup
this sets up Raid 1 on 2 identical disks

edit the script before running

1. fdisk -l to list your disks
2. find 2 devices
3. run the script

this will setup raid1 on dual disks - we use this with 2tb server grade nvme drives in fact.

https://wolf.uk.com

#use at your own risk

*** Note *** When you create a raid array it may take a couple of hours to sync you can check this with  

watch cat /proc/mdstatmd0 : active (auto-read-only) raid1 nvme3n1p1[1] nvme2n1p1[0]
      33520640 blocks super 1.2 [2/2] [UU]
        resync=PENDING
      
md2 : active raid1 nvme2n1p3[0] nvme3n1p3[1]
      465370432 blocks super 1.2 [2/2] [UU]
      bitmap: 2/4 pages [8KB], 65536KB chunk

md1 : active raid1 nvme3n1p2[1] nvme2n1p2[0]
      1046528 blocks super 1.2 [2/2] [UU]
      
md127 : active raid1 nvme0n1[0] nvme1n1[1]
      2000266560 blocks super 1.2 [2/2] [UU]
      [===========>.........]  resync = 55.3% (1107308672/2000266560) finish=73.8min speed=201585K/sec <<<< HERE you can see the sync happening. wait till its done
      bitmap: 7/15 pages [28KB], 65536KB chunk

unused devices: <none>



