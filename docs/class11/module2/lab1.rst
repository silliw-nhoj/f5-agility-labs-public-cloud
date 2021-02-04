F5 CloudFormation templates on Github
-------------------------------------

Open a new tab in the web browser. Click on the "PC101 AS3 Template" URL bookmark in the bookmark toolbar. An AS3 Declaration is a single JSON-formatted file that defines your virtual server(s) and all accompanying configuration objects. Some interesting configuration objects are highlighted in the screenshot below:

  - You use AWS tags to lookup the application pool members dynamically. You do not hardcode the IP addresses of pool members.
  - An HTTP/2 profile is enabled.
  - The Virtual Server Address is a "catch-all" wildcard address: 0.0.0.0/0.
  

.. image:: ./images/4a_f5_aws_cloudformation_as3_declaration.png
  :scale: 50%

Open another new tab in the web browser. Click on the "f5-aws-cloudformation" URL bookmark in the bookmark toolbar. Supported F5 CloudFormation templates are hosted on the official F5 GitHub repo: https://github.com/F5Networks/.

Scroll down and click on "Next"

.. image:: ./images/4_f5_aws_cloudformation_confirm_region2.png
  :scale: 50%

Fill in the CloudFormation template parameters. Leave defaults where not explicitly called out below.


+--------------------------------------------------------+------------------------------------------------------+
| Parameter                                              | Value                                                |
+========================================================+======================================================+
| **NETWORKING CONFIGURATION**                                                                                  |
+--------------------------------------------------------+------------------------------------------------------+
| VPC                                                    | (10.0.0.0/16)(terraform_student@f5lab.dev)           |
+--------------------------------------------------------+------------------------------------------------------+
| Management Subnet AZ1                                  | (10.0.101.0/24)(management)                          |
+--------------------------------------------------------+------------------------------------------------------+
| Management Subnet AZ2                                  | (10.0.102.0/24)(management)                          |
+--------------------------------------------------------+------------------------------------------------------+
| Subnet1 in AZ1                                         | (10.0.1.0/24)(public)                                |
+--------------------------------------------------------+------------------------------------------------------+
| Subnet1 in AZ2                                         | (10.0.2.0/24)(public)                                |
+--------------------------------------------------------+------------------------------------------------------+
| **INSTANCE CONFIGURATION**                                                                                    |
+--------------------------------------------------------+------------------------------------------------------+
| BIG-IP Image Name                                      | AdvancedWaf25Mbps                                    |
+--------------------------------------------------------+------------------------------------------------------+
| SSH Key                                                | MyKeyPair-student@f5lab.dev                          |
+--------------------------------------------------------+------------------------------------------------------+
| Source Address(es) for Management Access               | 0.0.0.0/0                                            |
+--------------------------------------------------------+------------------------------------------------------+
| Source Address(es) for Web Application Access (80/443) | 0.0.0.0/0                                            |
+--------------------------------------------------------+------------------------------------------------------+
| NTP Server                                             | 0.pool.ntp.org                                       |
+--------------------------------------------------------+------------------------------------------------------+
| Timezone (Olson)                                       | UTC                                                  |
+--------------------------------------------------------+------------------------------------------------------+
| BIG-IP Modules                                         | ltm:nominal,avr:nominal                              |
+--------------------------------------------------------+------------------------------------------------------+
| **VIRTUAL SERVICE CONFIGURATION**                                                                             |
+-------------------------------------------------+-------------------------------------------------------------+
| AS3 Declaration URL                             | https://f5-public-cloud.s3.amazonaws.com/pc101_as3_template |
+-------------------------------------------------+-------------------------------------------------------------+


.. image:: ./images/5_f5_aws_cloudformation_stack_details1.png
  :scale: 50%

.. image:: ./images/5_f5_aws_cloudformation_stack_details2.png
  :scale: 50%

Scroll to the bottom of the CloudFormation template and click [Next].

.. image:: ./images/5_f5_aws_cloudformation_stack_details3.png
  :scale: 50%

Click on "Estimate cost".

.. image:: ./images/7_f5_aws_cloudformation_estimate_cost1.png
  :scale: 50%

You can estimate the cost of running this CloudFormation stack with the AWS Simple Monthly Calculator. Review and close this screen.

.. image:: ./images/8_f5_aws_cloudformation_estimate_cost2.png
  :scale: 50%

Scroll to the bottom of the CloudFormation template. Acknowledge that AWS CloudFormation might create IAM resources and [Create stack].

.. image:: ./images/9_f5_aws_cloudformation_create_stack.png
  :scale: 50%

Watch as your resources are built in AWS by refreshing the CloudFormation Events screen.

.. image:: ./images/9_f5_aws_cloudformation_events.png
  :scale: 50%
