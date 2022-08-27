# Internet Gateway

We already have our VPC with 4 subnets, but none of those can access the Internet (they are effectively private). To turn 2 of them into public, we need to setup an [Internet Gateway](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Internet_Gateway.html) for our VPC and create a Route Table to route all external traffic through the gateway.
Finally, we need to associate 2 of our subnets to this route table and assign them a public IP, so they turn into public subnets.

## Create a Internet Gateway
1. Go to Internet Gateways on the left section.
2. Click Create Internet Gateway.
3. As Name tag put: `awsworkshopIGW`.
4. Click: Yes, Create.
5. Click Attach to VPC.
6. Click: Yes, Attach.

## Create Route tables
1. Go to Route Tables on the left section.
2. Click Create Route Table.
3. As Name tag: `awsWorkshopPublicRT`.
4. Click Yes, Create.
5. On the bottom section select the Routes tab.
6. Click on Edit button.
7. Click on Add another Route.
8. As **Destination** put `0.0.0.0/0`.
9. As **Target** select your Internet Gateway.
10. Click Save.
11. Now select Subnet Associations tab.
12. Click on Edit.
13. Select `10.0.1.0-us-east-1a` and `10.0.3.0-us-east-1b`.
14. Click Save.

## Assign public IP to our public subnet
1. Go to Subnets on the left section.
2. Select the `10.0.1.0-us-east-1a`.
3. Click on Subnet Actions.
4. Select Modify auto-assign IP settings.
5. Check: Enable auto-assign public IPv4 address.
6. Click Save.
7. Click Close.
8. Repeat steps 2-7 with `10.0.3.0-us-east-1b`.

---
**Next:** [create a NAT Instance](/workshop/vpc-subnets-bastion/03-nat-instance.md).
