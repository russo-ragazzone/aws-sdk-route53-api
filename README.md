# Notes

The amazon route53 php-api class was initially implemented by [mshanken](https://github.com/mshanken) \([aws-sdk-for-php repo](https://github.com/mshanken/aws-sdk-for-php/)\).
But the old version doesn't work with the current API version \(2012-02-29\), and this version does. So, if you want support for the Amazon Route53 API in your SDK,
simply put the file route53.class.php into your SDK folder/services

### Usage example:

	$route53 = new AmazonRoute53();

	# List hosted zones:
	$response = $route53->list_hosted_zone();

	$zone_id = reset($response->body->Id()->map_string());
	$zone_id = str_replace('/hostedzone/', '',$zone_id);
	$response = $route53->list_resource_record_sets($zone_id, array('Type' => 'CNAME', 'Name' => $name, 'MaxItems' => 1));


All existing Route53 API methods are supported.
