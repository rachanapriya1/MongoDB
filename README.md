
//Write a MongoDb query to update grade B to A in all documents.
db.restaurant.updateMany({ "grades.grade": "B" }, { $set: { "grades.$.grade": "A" } });

// Write a MongoDB query to find the restaurant name, longitude and latitude and cuisine for those restaurants which contain 'Caf' as first three letters of its name.
db.restaurant.find(
                   { name : 
                     { $regex : "caf.*", $options: "i" } 
                   },
                       {
                         "name":1,
                         "borough":1,
                         "cuisine" :1
                        }
                   );

//Write a MongoDB query to find the restaurants that achieved a score, more than 80 but less than 100.
db.restaurant.find({grades : { $elemMatch:{"score":{$gt : 8 , $lt :10}}}});

//Write a MongoDB query to find the restaurants who achieved a score more than 90.
db.restaurant.find({grades : { $elemMatch:{"score":{$gt : 9}}}});

//Write a MongoDB query to display the next 5 restaurants after skipping first 5.
db.restaurant.find().skip(5).limit(5);

//Write a MongoDB query to display the first 5 restaurant in ascending order of name field.
db.restaurant.find().limit(5);

//Write a MongoDB query to arrange the name of the restaurants in ascending order along with all the columns
db.restaurant.find().sort({ name: 1 });

//Write a MongoDB query to display the fields restaurant_id, name, and zip code but exclude the field _id for all the documents in the collection restaurant
db.restaurant.find({},{"restaurant_id" : 1,"name":1,"address.zipcode" :1,"_id":0});
