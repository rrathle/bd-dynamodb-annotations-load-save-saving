### DynamoDBSave Pre-work

**Branch name:** annotationsloadsave-prework

**AWS account:** (account number for your <Alias>ATAUnit3 account -- 
[find on Conduit](https://access.amazon.com/aws/accounts))
 
**role:** IibsAdminAccess-DO-NOT-DELETE

Expected time required: 20 min

In this coding activity, you will get practice saving and updating items using the DynamoDB table
`DynamoDbAnnotationsLoadSave-Books`. The table keeps track of a few different attributes (no doubt a
small subset of the true book catalog, but suitable for our needs here).

NOTE: This activity uses data in your personal AWS account, not the
shared account we've used in class.

#### Book POJO

A `Book` POJO based on the `DynamoDbAnnotationsLoadSave-Books` DynamoDB table. Has been provided for you.
It should match your solution to the `annotations` try.

The Books table can be found in your AWS Console and is set-up
the following way:

| asin       | author  | title              | year_published |
|------------|---------|--------------------|----------------|
| B00EGMV00W | Baldwin | The Fire Next Time | 1963           |

#### BookDao

Code for `getBook()` has been provided for you. It should match your solution to
the `load01` try.

Write code for the `saveBook()` method in the `BookDao` class. The `saveBook()`
method should accept an instance of `Book` and save it to the table.

#### Complete the test

Find the integration test under the `src/integrationTest/java` directory.
The full classname is `BookIntegrationTests`

Update the `BookIntegrationTests` class
to instantiate an actual `DynamoDBMapper` instance, including getting
a client via the `DynamoDbClientProvider` class mentioned in the
[DynamoDB Load reading](https://code.amazon.com/packages/ATACurriculum_LearningMaterials/blobs/mainline/--/dynamodb_annotations_load_save/02_dynamodb_loading.md#dynamodbclientprovider-class)
(Reminder: `DynamoDbClientProvider` is a utility that ATA provides from the
`ATAResources` package)

Now, run the test class manually in IntelliJ and make sure you get everything passing.

This test actually saves/retrieves data from the DynamoDB table. This is why
we're calling it an integration test (if it were a unit test, we'd put it in
`src/test/java/...` and we'd be mocking the `DynamoDBMapper` we pass into the DAO).

You can see what happens if you delete/alter the book item in DynamoDB
that the test expects to be there. You can use the DynamoDB Console for this,
to change the items, just make sure you know what to put back in afterwards to restore
the data.

**HINT:** see the `cloudformation/dynamodbannotationsloadsave/prework/BooksTable.yaml`
file that was used to create the table and sample data in your AWS Account, then
manually modify to get it back to where it was.

#### Test away!

Once you've written `saveBook()` in `BookDao` and updated `BookIntegrationTests`,
you should be able to pass the tests set-up in the `BookIntegrationTests` class,
which is located in `src/integrationTest/java/com/amazon/ata/dynamodbannotationsloadsave/prework/`.

Reminder: You can run the full test class manually by right-clicking the file in the project view and
selecting "Run 'BookIntegrationTests'", or by clicking the double arrows to the left of the class declaration
when viewing `BookIntegrationTests`.

**You have completed this pre-work when:**
* You have implemented the `saveBook()` method in the `BookDao` class.
* You have updated `BookIntegrationTests` to instantiate a `DynamoDBMapper` instance.
* The `BookIntegrationTests` are passing.
* You have committed and pushed your code.
* You have answered the Canvas quiz with a link to your commit on code browser.

**HINT:**
* [The table attributes won't map to my POJO and I don't know why!](./hints/hint-01.md)
* [The getXXX() method isn't finding the correct item or is giving me an error!](./hints/hint-02.md)
