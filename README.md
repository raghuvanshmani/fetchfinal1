# fetchfinal1
from tkinter import *
import pymongo
from  tkinter import colorchooser
root =Tk()
n = StringVar()
a= StringVar()
q=StringVar()
nu=IntVar()
g=StringVar()
def create():
    uri = "mongodb://127.0.0.1:27017"
    connection = pymongo.MongoClient(uri)
    database = connection['Ragistration']
    collection = database['student']
    data = {"age":23}
    collection.insert_one(data)
def insert():
    uri = "mongodb://127.0.0.1:27017"
    connection = pymongo.MongoClient(uri)
    database = connection['Ragistration']
    collection = database['student']
    data = [
        {"name":n.get()},
        {"address":a.get()},
        {"qualification":q.get()},
        {"number":nu.get()},
        {"gender":g.get()}

    ]
    collection.insert_many(data)
def change_color():
    clr=colorchooser.askcolor()
    root.configure(background=clr[1])




def fetch():
    top=Toplevel()
    top.geometry('600x600')
    top.title("fetch the data")
    text=Text(top,font=10)
    text.pack(fill=BOTH,expand=1)
    text.delete(1.0,END)


    uri = "mongodb://127.0.0.1:27017"
    connection = pymongo.MongoClient(uri)
    database = connection['Ragistration']
    collection = database['student']
    x = collection.find()
    for i in x:
        text.insert(INSERT,i)
        print()












de= Button(root,text="delete",font=10,activebackground="yellow",activeforeground="red")

de.grid(row=7,column=4)

bt= Button(root,text="change color",font=10,command=change_color)
bt.grid(row=15,column=0)
cr = Button(root,text="create",font=10,activebackground="yellow",
activeforeground="red",command=create)
cr.grid(row=7,column=0)
ins = Button(root,text="insert",font=10,activebackground="yellow",
activeforeground="red",command=insert)
ins.grid(row=7,column=2)
fet = Button(root,text="fetch",font=10,activebackground="yellow",
activeforeground="red",command=fetch)
fet.grid(row=7,column=3)


root.title("Ragitrationform")
name = Label(root ,text="Name",bg="white",font = 20,bd=4,fg="green")
name.grid(row = 0,column= 0)
namee=Entry(root,font=10,bg="white",textvariable=n)
namee.grid(row=0,column=3)
addr = Label(root ,text="Address",bg="white",font = 20,bd=4,fg="green")
addr.grid(row = 1,column= 0)
addre = Entry(root,font=20,bg="white",textvariable=a)
addre.grid(row=1,column=3)
quali = Label(root ,text="Qualification",bg="white",font = 20,bd=4,fg="red")
quali.grid(row = 2,column= 0)
qualie = Entry(root,font=20,bg="white",textvariable=q)
qualie.grid(row=2,column=3)
number = Label(root ,text="Mobile Number",bg="white",font = 20,bd=4,fg="red")
number.grid(row = 3,column= 0)
numbere = Entry(root,font=20,bg="white",textvariable=nu)
numbere.grid(row=3,column=3)
gender = Label(root ,text="gender",bg="white",font = 20,bd=4,fg="red")
gender.grid(row = 4,column= 0)
gendere = Entry(root,font=20,bg="white",textvariable=g)
gendere.grid(row=4,column=3)
root.geometry('600x600')
root.mainloop()
