# Indian GSTIN Check Using Zoho Deluge

>How to do Proper Indian GSTIN Number Validation using Deluge Function in ZohoHow to do Proper Indian GSTIN Number Validation using Deluge Function in Zoho

Hi, This is Sayan.

In this repo I have shared an example function deluge code (snippet) which will **help you to instantly check the correctness of a Indian Goods & Services Tax Identication Number. To prevent users from unknowingly entering wrong GSTIN Numbers in the system other than Zoho Books where we do not have any in-built checking for the input.**

This code can be helpful in the below scenarios:
- User Entering GSTIN number in Zoho Creator Custom Application
- User Onboarding Customer in Zoho CRM Environment
- Service Vendor's Details on Zoho Project
- Onboarding Vendor in Zoho Books from a Third Party Application


## To create the validation:
### Step 1 -
Create a Workflow upon which the Function should be called with proper conditions, and make sure to pass the GSTIN Input which will be checked for validation
### Step 2 -
Use Map(); as the return value so that this Function can return more data in future
### Step 3 -
Paste the below Code in the Function:
---
map GET_validation(string GSTIN)
   {
   	format = matches(GSTIN,"[0-9]{2}[A-Z]{5}[0-9]{4}[A-Z]{1}[1-9A-Z]{1}" + 'Z' + "[1-9A-Z]{1}");
   	response = Map();
   	if(GSTIN.isNull())
   	{
   		response.put('status','Failed');
   		response.put('message','The GSTIN field cannot be left Empty');
   	}
   	else
   	{
   		if(GSTIN.length() != 15)
   		{
   			response.put('status','Failed');
   			response.put('message','The GSTIN entered must be 15 Characters');
   		}
   		else if(GSTIN.length() == 15 && format == true)
   		{
   			response.put('status','success');
   		}
   		else
   		{
   			response.put('status','Failed');
   			response.put('message','Please enter a valid GSTIN number');
   		}
   	}
   	return response;
}
---
### Step 4 -
Now You can call the function with the String Value passed as "GSTIN", so that you the deluge code can validate the same and return the values.