## Sending Log Data from kinesis agent to Kinesis DataStreams for AWS CloudFormation

This Cloudformation create necessary resources to send logs to kinesis and send from kinesis to another resources.

## Folder Structure

```
.
├── README.md
├── build
│   ├── alert.zip          # bring from repository go(WIP)
│   ├── senderrorlog.zip   # bring from repository go(WIP)
│   └── sendlog.zip        # bring from repository go(WIP)
├── cloudformation.yml
├── cloudwatch-alarm.yml
├── elasticsearch.yml
├── kinesis-data-streams.yml
├── lambda-role.yml
├── lambda.yml
└── sns.yml

```

## Create Stack
```
S3_BUCKET=bucket-name

aws cloudformation package --template-file cloudformation.yml --s3-bucket ${S3_BUCKET} --s3-prefix log-stack --output-template-file .packaged.yml
aws cloudformation deploy --template-file .packaged.yml --stack-name log-stack --capabilities CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND
```

## Delete Stack
```
aws cloudformation delete-stack --stack-name <stack-name>
```

## Cancel creation
```
aws cloudformation cancel-update-stack --stack-name <stack-name>
```

## Properties

SSM Parameter Types
Parameters that correspond to existing parameters in Systems Manager Parameter Store. You specify a Systems Manager parameter key as the value of the SSM parameter, and AWS CloudFormation fetches the latest value from Parameter Store to use for the stack. For more information, see SSM Parameter Types.
AWS CloudFormation doesn't currently support the SecureString Systems Manager parameter type.
