COMPUTER NETWORKS – 21CSC302J
Computer Network Lab Exam: LAN and WAN Configuration Objective Create and configure a suitable topology for both LAN and WAN using 10-15 computers, routers, and switches. Simulate the transmission of a message from one network to a computer in another network.

Topology Design
#LAN 1: ● IP Range: 192.168.1.0/24 ● Devices: 5 PCs ● Switch: Switch 1 ● Router: Router 1

LAN 2:
● IP Range: 192.168.2.0/24 ● Devices: 5 PCs ● Switch: Switch 2 ● Router: Router 2

WAN:
● IP Range: 10.0.0.0/30 (Point-to-Point Connection) ● Connection: Between Router 1 and Router 2 Step-by-Step Procedure Step 1: Topology Setup

Add Devices:
● LAN 1: ○ 5 PCs, 1 switch (Switch 1), 1 router (Router 1).

● LAN 2: ○ 5 PCs, 1 switch (Switch 2), 1 router (Router 2).

● WAN: ○ Serial DCE cable connection between Router 1 and Router 2.

Connect Devices:
● LAN 1: ○ Connect each PC to Switch 1 using a Copper Straight-Through cable. ○ Connect Switch 1 to Router 1's GigabitEthernet0/0 interface.

● LAN 2: ○ Connect each PC to Switch 2 using a Copper Straight-Through cable. ○ Connect Switch 2 to Router 2's GigabitEthernet0/0 interface.

● WAN Connection: ○ Use the Serial DCE cable to connect Serial0/0/0 on Router 1 to Serial0/0/0 on Router 2.

Step 2: IP Address Assignment

LAN 1: ● PC1: 192.168.1.2 / 255.255.255.0 / Gateway: 192.168.1.1 ● PC2: 192.168.1.3 / 255.255.255.0 / Gateway: 192.168.1.1 ● PC3: 192.168.1.4 / 255.255.255.0 / Gateway: 192.168.1.1 ● PC4: 192.168.1.5 / 255.255.255.0 / Gateway: 192.168.1.1 ● PC5: 192.168.1.6 / 255.255.255.0 / Gateway: 192.168.1.1

Router 1 Configuration: enable configure terminal interface GigabitEthernet0/0 ip address 192.168.1.1 255.255.255.0 no shutdown exit interface Serial0/0/0 ip address 10.0.0.1 255.255.255.252 clock rate 64000 no shutdown exit write memory

LAN 2: ● PC6: 192.168.2.2 / 255.255.255.0 / Gateway: 192.168.2.1 ● PC7: 192.168.2.3 / 255.255.255.0 / Gateway: 192.168.2.1 ● PC8: 192.168.2.4 / 255.255.255.0 / Gateway: 192.168.2.1 ● PC9: 192.168.2.5 / 255.255.255.0 / Gateway: 192.168.2.1 ● PC10: 192.168.2.6 / 255.255.255.0 / Gateway: 192.168.2.1

Router 2 Configuration: enable configure terminal interface GigabitEthernet0/0 ip address 192.168.2.1 255.255.255.0 no shutdown exit interface Serial0/0/0 ip address 10.0.0.2 255.255.255.252 no shutdown exit write memory

Step 3: Configure Routing

Router 1 Static Route: configure terminal ip route 192.168.2.0 255.255.255.0 10.0.0.2 exit write memory Router 2 Static Route: configure terminal ip route 192.168.1.0 255.255.255.0 10.0.0.1 exit write memory Step 4: Test Connectivity Ping Test: From PC1 (192.168.1.2), ping PC6 (192.168.2.2): ping 192.168.2.2 The ping should be successful, indicating that the WAN connection between LAN 1 and LAN 2 is functioning correctly.
