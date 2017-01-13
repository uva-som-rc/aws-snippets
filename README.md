# aws-snippets
A collection of snippets for interacting with AWS via Python/boto3

## Installations:
`pip install boto3`

`pip install botocore` - Necessary for error handling

`pip install awscli` - Useful for console and bash scripting.

`sudo apt-get install jq / yum install jq` - Useful for parsing JSON via bash/console.

## Credentials
boto3 can make use of (at least) three levels of authentication:

1. Hard-coded key/secret key within your application (NEVER use in production).

    import boto3
    client = boto3.client(
        's3',
        aws_access_key_id=ACCESS_KEY,
        aws_secret_access_key=SECRET_KEY,
        aws_session_token=SESSION_TOKEN,
    )

2. An application or server-level config file containing the key/secret key. Useful especially if you have multiple account profiles to juggle (EXCLUDE this from git).

    # Example ~/.aws/config file.
    [default]
    aws_access_key_id=foo
    aws_secret_access_key=bar

3. Environment variables. Simply populate these two vars for your shell (Good for local development off of EC2).

    AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY

4. An IAM role specifically tailored to the EC2 instance running the code (Best practice).

The Python snippets in this collection assume you are using option 2, 3 or 4 for authentication. More information about their setup can be found at:

http://boto3.readthedocs.io/en/latest/guide/configuration.html

