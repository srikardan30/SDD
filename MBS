from tkinter import*
from random import *
import time

class IntEntry(Entry):
    def __init__(self, master=None, **kwargs):
        self.var = StringVar()
        Entry.__init__(self, master, textvariable=self.var, **kwargs)
        self.old_value = ''
        self.var.trace('w', self.check)
        self.get, self.set = self.var.get, self.var.set

    def check(self, *args):
        if self.get().isdigit():
            # the current value is only digits; allow this
            self.old_value = self.get()
            print(self.old_value)
        else:
            # there's non-digit characters in the input; reject this
            self.set('')

class WinDos:

    def __init__(self,mainWin):
        self.data_store = {}
        self.mainWin = mainWin
        self.mainWin.configure(bg="white") #simply to change the colour of the frame
###################################################################################################################
#MAIN PAGE CODE

#below are the texts and buttons that will appear on the home screen/main page for the users to then navigate
        
        self.homepage_text1= Label(self.mainWin, text="Welcome to the HBHS Motel™", bg='white', font=("Calibri", 20, 'bold'))
        self.homepage_text1.grid(row=2, column=2)
        
        self.homepage_text2= Label(self.mainWin, text="Please choose your desired option", bg='white', font=("Calibri", 15))
        self.homepage_text2.grid(row=3, column=2)

        self.refer_to_guide3 = Label(self.mainWin, text="Please refer to GUIDE if unsure", font=("Calibri", 10), bg='white')
        self.refer_to_guide3.grid(row=4, column=2)

        button_instructions = Button(self.mainWin, text="GUIDE", bg='white', font=("Calibri", 14, 'bold'), command=self.instructionsPage)
        button_instructions.grid(row=5, column=2, padx=5, pady=5)
        
        button_checkIn = Button(self.mainWin, text="CHECK IN", bg='white', font=("Calibri", 14, 'bold'), command=self.checkInPage)
        button_checkIn.grid(row=6, column=2, padx=5, pady=5)
        
        button_checkOut = Button(self.mainWin, text="CHECK OUT", bg='white', font=("Calibri", 14, 'bold'), command=self.checkOutPage)
        button_checkOut.grid(row=7, column=2, padx=5, pady=5)
         
        button_help = Button(self.mainWin, text='HELP PAGE', bg='white', font=("Calibri", 14, 'bold'), command=self.helpPage)
        button_help.grid(row=8, column=2, padx=5, pady=5)

#submission page for check in page
        self.submissionWin_check_in = Toplevel()
        self.submissionWin_check_in.configure(bg='white')
        
        self.check_in_submission_title = Label(self.submissionWin_check_in, text="Confirmation Page", font=("Calibri", 20, 'bold'), bg='white')
        self.check_in_submission_title.grid(row=1, column=1)

        self.user_name = Label(self.submissionWin_check_in, bg='white', font=("Calibri", 12, 'bold'))
        self.user_name.grid(row=2, column=1, padx=5, pady=5)

        self.user_gender_ci = Label(self.submissionWin_check_in, bg='white', text='', font=("Calibri", 12))
        self.user_gender_ci.grid(row=3, column=1, padx=5, pady=5)

        self.how_many_people = Label(self.submissionWin_check_in, bg='white', text='', font=("Calibri", 12))
        self.how_many_people.grid(row=4, column=1, padx=5, pady=5)

        self.user_room_type_ci = Label(self.submissionWin_check_in, bg='white', text='', font=("Calibri", 12))
        self.user_room_type_ci.grid(row=5, column=1, padx=5, pady=5)

        self.stay_of_user = Label(self.submissionWin_check_in, bg='white', font=("Calibri", 12))
        self.stay_of_user.grid(row=6, column=1, padx=5, pady=5)

        self.user_room_number = Label(self.submissionWin_check_in, bg='white', font=("Calibri", 12, 'bold'))
        self.user_room_number.grid(row=7, column=1, padx=5, pady=5)

        self.selected_options2 = Label(self.submissionWin_check_in, bg='white', font=("Calibri", 12), text='Selected add-ons:')
        self.selected_options2.grid(row=8, column=1, padx=5, pady=5)

        self.selected_options = Label(self.submissionWin_check_in, text='', bg='white', font=("Calibri", 12))
        self.selected_options.grid(row=9, column=1)
        
        self.submission_to_main = Button(self.submissionWin_check_in, text="OK", command=self.confirmToCheckIn, font=("Calibri", 12, 'bold'), bg='white')
        self.submission_to_main.grid(row=10, column=1)

        self.submissionWin_check_in.protocol("WM_DELETE_WINDOW", self.closepage)
        self.submissionWin_check_in.withdraw()

#submission page for check out page
        self.submissionWin_check_out = Toplevel()
        self.submissionWin_check_out.configure(bg='white')

        self.check_out_submission_title = Label(self.submissionWin_check_out, text='Payment Page', font=("Calibri", 20, 'bold'), bg='white')
        self.check_out_submission_title.grid(row=1, column=1)

        self.total_payment = Label(self.submissionWin_check_out, text='', bg='white', font=("Calibri", 14, 'bold'))
        self.total_payment.grid(row=2, column=1)

        self.type_of_payment = Label(self.submissionWin_check_out, text='', bg='white', font=("Calibri", 12))
        self.type_of_payment.grid(row=4, column=1, padx=10, pady=10)

        self.user_message = Label(self.submissionWin_check_out, text='Please complete the payment at the main desk',bg='white', font=("Calibri", 12))
        self.user_message.grid(row=5, column=1)

        self.user_message2 = Label(self.submissionWin_check_out, text='We hope you enjoyed your stay at the HBHS Motel™',bg='white', font=("Calibri", 12))
        self.user_message2.grid(row=6, column=1)

        self.user_message3 = Label(self.submissionWin_check_out, text='Come back soon!',bg='white', font=("Calibri", 12))
        self.user_message3.grid(row=7, column=1)

        self.payment_to_main = Button(self.submissionWin_check_out, text='HOME PAGE', command=self.paymentToMain, font=("Calibri", 12, 'bold'), bg='white')
        self.payment_to_main.grid(row=8, column=1)

        self.submissionWin_check_out.protocol("WM_DELETE_WINDOW", self.closepage)
        self.submissionWin_check_out.withdraw()              
###################################################################################################################
#CHECK IN PAGE CODE    
        self.secondWin = Toplevel()
        self.secondWin.configure(bg="white")
        
        #title for the page (label widget)
        self.check_in_title = Label(self.secondWin, text="Check In Page", font=("Calibri", 20, 'bold'), bg='white')
        self.check_in_title.grid(row=1, column=1)

        self.refer_to_guide = Label(self.secondWin, text="Please refer to GUIDE if unsure", font=("Calibri", 10), bg='white')
        self.refer_to_guide.grid(row=2, column=1)
        
        #label widget for first name
        self.first_name = Label(self.secondWin, text="Full name(s)", bg='white', font=("Calibri", 12, 'bold'))
        self.first_name.grid(row=3, column=1, padx=10, pady=10)

        #created a frame for all the buttons to be in
        self.name_frame = Frame(self.secondWin)
        self.name_frame.grid(row=4, column=1)

        #entry widget for first name
        self.first_name_entry = Entry(self.name_frame, width=25)
        self.first_name_entry.grid(row=4, column=1)
        
        #label widget for gender
        self.user_gender = Label(self.secondWin, text='Gender', bg='white', font=("Calibri", 12, 'bold'))
        self.user_gender.grid(column=1, row=5, padx=10, pady=10)
        
        #radio button for gender
        self.var = IntVar()

        #created a frame for all the buttons to be in
        self.gender_button_frame = Frame(self.secondWin)
        self.gender_button_frame.grid(row=6, column=1)

        #for male
        self.user_gender_male = Radiobutton(self.gender_button_frame, text='Male', variable=self.var, value = 1, bg="white", font=("Calibri", 12))
        self.user_gender_male.grid(column=1, row=6)
        
        #for female
        self.user_gender_female = Radiobutton(self.gender_button_frame, text='Female', variable=self.var, value = 2, bg="white", font=("Calibri", 12))
        self.user_gender_female.grid(row=6, column=2)
        
        #for those who dont want to say
        self.user_gender_nil = Radiobutton(self.gender_button_frame, text='Prefer not to say', variable=self.var, value = 3, bg="white", font=("Calibri", 12))
        self.user_gender_nil.grid(row=6, column=3)
        
        #label widget for the number of people
        self.occupant = Label(self.secondWin, text='Number of occupants', bg='white', font=("Calibri", 12, 'bold'))
        self.occupant.grid(row=7, column=1, padx=10, pady=10)

        #created a frame for all the buttons to be in
        self.occupants_number_frame1 = Frame(self.secondWin)
        self.occupants_number_frame1.grid(row=8, column=1)

        self.var8 = IntVar()
        self.occupant_1 = Radiobutton(self.occupants_number_frame1, text='1', bg='white', variable=self.var8, value=1, font=("Calibri", 12))
        self.occupant_1.grid(row=8, column=1)
        self.occupant_2 = Radiobutton(self.occupants_number_frame1, text='2', bg='white', variable=self.var8, value=2, font=("Calibri", 12))
        self.occupant_2.grid(row=8, column=2)
        self.occupant_3 = Radiobutton(self.occupants_number_frame1, text='3', bg='white', variable=self.var8, value=3, font=("Calibri", 12))
        self.occupant_3.grid(row=8, column=3)
        self.occupant_4 = Radiobutton(self.occupants_number_frame1, text='4', bg='white', variable=self.var8, value=4, font=("Calibri", 12))
        self.occupant_4.grid(row=8, column=4)
        
        #label widget for length of stay
        self.stay_length = Label(self.secondWin, text="Length of Stay (max 60 days)", bg="white", font=("Calibri", 12, 'bold'))
        self.stay_length.grid(row=9, column=1, padx=10, pady=10)

        #created a frame for all the buttons to be in
        self.stay_length_frame = Frame(self.secondWin)
        self.stay_length_frame.grid(row=10, column=1)

        #entry widget for length of stay
        self.stay_length_number = IntEntry(self.stay_length_frame, width=5)
        self.stay_length_number.grid(row=10, column=1)

        #label widget for choice of room
        self.room_type = Label(self.secondWin, text='Room type', bg='white', font=('Calibri', 12, 'bold'))
        self.room_type.grid(row=11, column=1, padx=10, pady=10)

        #created a frame for all the buttons to be in
        self.room_type_frame = Frame(self.secondWin)
        self.room_type_frame.grid(row=12, column=1)
        self.room_type_frame2 = Frame(self.secondWin)
        self.room_type_frame2.grid(row=13, column=1)

        #radio button for room type
        self.var1 = IntVar()
        self.room_type_option1 = Radiobutton(self.room_type_frame, text='Single Suite', bg='white', variable=self.var1, value=40, font=("Calibri", 12))
        self.room_type_option1.grid(row=12, column=1)
        #radio button for room type
        self.room_type_option2 = Radiobutton(self.room_type_frame, text='Double Suite', bg='white', variable=self.var1, value=60, font=("Calibri", 12))
        self.room_type_option2.grid(row=12, column=2)
        #radio button for room type
        self.room_type_option3 = Radiobutton(self.room_type_frame2, text='Queen Suite', bg='white', variable=self.var1, value=100, font=("Calibri", 12))
        self.room_type_option3.grid(row=13, column=3)
        #radio button for room type
        self.room_type_option4 = Radiobutton(self.room_type_frame2, text='Executive Suite', bg='white', variable=self.var1, value=150, font=("Calibri", 12))
        self.room_type_option4.grid(row=13, column=4)

        #label widget for additional items
        self.additional_add_ons = Label(self.secondWin, text='Additional add-ons', bg='white', font=('Calibri', 12, 'bold'))
        self.additional_add_ons.grid(row=14, column=1, padx=10, pady=10)

        #created a frame for all the buttons to be in
        self.additional_add_ons_frame = Frame(self.secondWin)
        self.additional_add_ons_frame.grid(row=15, column=1)
        self.additional_add_ons_frame2 = Frame(self.secondWin)
        self.additional_add_ons_frame2.grid(row=16, column=1)
        self.additional_add_ons_frame3 = Frame(self.secondWin)
        self.additional_add_ons_frame3.grid(row=17, column=1)
        
        #check button for additional items
        self.var2 = IntVar()
        self.additional_add_ons1 = Checkbutton(self.additional_add_ons_frame, text='WiFi', bg='white', variable=self.var2, font=("Calibri", 12))
        self.additional_add_ons1.grid(row=15, column=1)
        
        #check button for additional items
        self.var3 = IntVar()
        self.additional_add_ons2 = Checkbutton(self.additional_add_ons_frame, text='Pool access', bg='white', variable=self.var3, font=("Calibri", 12))
        self.additional_add_ons2.grid(row=15, column=2)
        
        #check button for additional items
        self.var4 = IntVar()
        self.additional_add_ons3 = Checkbutton(self.additional_add_ons_frame2, text='Parking', bg='white', variable=self.var4, font=("Calibri", 12))
        self.additional_add_ons3.grid(row=16, column=1)
        
        #check button for additional items
        self.var5 = IntVar()
        self.additional_add_ons4 = Checkbutton(self.additional_add_ons_frame2, text='Room service', bg='white', variable=self.var5, font=("Calibri", 12))
        self.additional_add_ons4.grid(row=16, column=2)
        
        #check button for additional items
        self.var6= IntVar()
        self.additional_add_ons5 = Checkbutton(self.additional_add_ons_frame3, text='AC', bg='white', variable=self.var6, font=("Calibri", 12))
        self.additional_add_ons5.grid(row=17, column=1)
        
        #check button for additional items
        self.var7 = IntVar()
        self.additional_add_ons6 = Checkbutton(self.additional_add_ons_frame3, text='TV', bg='white', variable=self.var7, font=("Calibri", 12))
        self.additional_add_ons6.grid(row=17, column=2)

        #incorrect details label
        self.incorrect_message_label = Label(self.secondWin, text='', bg='white', font=('Calibri', 12, 'bold'))
        self.incorrect_message_label.grid(row=18, column=1)

        #created a frame for all the buttons to be in
        self.submit_details_check_in_frame = Frame(self.secondWin)
        self.submit_details_check_in_frame.grid(row=19, column=1)

        #submission button
        self.submit_details_check_in = Button(self.submit_details_check_in_frame, text="SUBMIT", bg="white", command=self.submitToConfirm, font=("Calibri", 12, 'bold'))
        self.submit_details_check_in.grid(row=19,column=1)
        
        #created a frame for all the buttons to be in
        self.exit_check_in_frame = Frame(self.secondWin)
        self.exit_check_in_frame.grid(row=20, column=1)

        #go back button
        self.exit_check_in = Button(self.exit_check_in_frame, text="BACK", bg="white", command=self.checkInToHome, font=("Calibri", 12, 'bold'))
        self.exit_check_in.grid(row=20, column=1)

        self.secondWin.withdraw()  # Hide this window until we need it!
        self.secondWin.protocol("WM_DELETE_WINDOW", self.endProgram)
###################################################################################################################
#CHECK OUT PAGE CODE

        self.thirdWin = Toplevel()
        self.thirdWin.configure(bg="white")

        #title for the page (label widget)
        self.check_out_title = Label(self.thirdWin, text="Check Out Page", font=("Calibri", 20, 'bold'), bg='white')
        self.check_out_title.grid(row=1, column=1)

        self.refer_to_guide2 = Label(self.thirdWin, text="Please refer to GUIDE if unsure", font=("Calibri", 10), bg='white')
        self.refer_to_guide2.grid(row=2, column=1)

        #label widget for name
        self.check_out_name_label = Label(self.thirdWin, text="Name: ", font=('Calibri', 12, 'bold'), bg='white')
        self.check_out_name_label.grid(row=3, column=1)

        self.check_out_name_frame = Frame(self.thirdWin)
        self.check_out_name_frame.grid(row=4, column=1)

        #entry widget for name
        self.check_out_name = Entry(self.check_out_name_frame, width=25)
        self.check_out_name.grid(row=4, column=1)

        #label widget for room number
        self.room_number_label = Label(self.thirdWin, text='Room No: ', font=('Calibri', 12, 'bold'), bg='white')
        self.room_number_label.grid(row=5, column=1)

        self.room_number_frame = Frame(self.thirdWin)
        self.room_number_frame.grid(row=6, column=1)

        #entry widget for room number
        self.room_number = IntEntry(self.room_number_frame, width=10, bg='white')
        self.room_number.grid(row=6, column=1)

        #label widget for payment option
        self.payment = Label(self.thirdWin, text="Payment option: ", bg="white", font=('Calibri', 12, 'bold'))
        self.payment.grid(row=7, column=1)

        self.payment_options_frame = Frame(self.thirdWin)
        self.payment_options_frame.grid(row=8, column=1)
           
        #radio button widget for payment option
        #radio button widget for cash payments
        self.var9 = IntVar()
        self.payment_option1 = Radiobutton(self.payment_options_frame, text="Cash", variable=self.var9, value=1, bg="white", font=("Calibri", 12))
        self.payment_option1.grid(row=8, column=1)
        
        #radio button widget for card payments
        self.payment_option2 = Radiobutton(self.payment_options_frame, text="Card", variable=self.var9, value=2, bg="white", font=("Calibri", 12))
        self.payment_option2.grid(row=8, column=2)
        
        #radio button widget for other payments
        self.payment_option3 = Radiobutton(self.payment_options_frame, text="Other", variable=self.var9, value=3, bg="white", font=("Calibri", 12))
        self.payment_option3.grid(row=8, column=3)

        self.message_label = Label(self.thirdWin, text='', bg='white', font=('Calibri', 12, 'bold'))
        self.message_label.grid(row=9, column=1)

        self.submit_details_frame = Frame(self.thirdWin)
        self.submit_details_frame.grid(row=10, column=1)

        #submit details button
        self.submit_details_check_out = Button(self.submit_details_frame, text="SUBMIT", bg='white', font=("Calibri", 12, 'bold'), command=self.submitToPayment)
        self.submit_details_check_out.grid(row=10, column=1)

        self.exit_check_out_frame = Frame(self.thirdWin)
        self.exit_check_out_frame.grid(row=11, column=1)
        
        #go back button
        self.exit_check_out = Button(self.exit_check_out_frame, text="BACK", command=self.checkOutToHome, bg='white', font=("Calibri", 12, 'bold'))
        self.exit_check_out.grid(row=12, column=1)

        self.thirdWin.withdraw()  # Hide this window until we need it!
        self.thirdWin.protocol("WM_DELETE_WINDOW", self.endProgram)         
###################################################################################################################
#INSTRUCTIONS PAGE CODE

        self.fourthWin = Toplevel()
        self.fourthWin.configure(bg="white")

        #title for the page (label widget)
        self.instructions_title = Label(self.fourthWin, text="Instructions Page", font=("Calibri", 20, 'bold'), bg='white')
        self.instructions_title.grid(row=1, column=1)

        self.instructions_message = Label(self.fourthWin, text="How to CHECK IN", font=("Calibri", 12), bg='white')
        self.instructions_message.grid(row=2, column=1)

        self.instructions_message_button = Button(self.fourthWin, text='CHECK IN', bg='white', font=("Calibri", 14, 'bold'), command=self.checkInInstructions)
        self.instructions_message_button.grid(row=3, column=1, padx=10, pady=10)

        self.instructions_message2 = Label(self.fourthWin, text="How to CHECK OUT", font=("Calibri", 12), bg='white')
        self.instructions_message2.grid(row=4, column=1)

        self.instructions_message2_button = Button(self.fourthWin, text='CHECK OUT', bg='white', font=("Calibri", 14, 'bold'), command=self.checkOutInstructions)
        self.instructions_message2_button.grid(row=5, column=1, padx=10, pady=10)
        
        #go back button
        self.exit_instructions = Button(self.fourthWin, text="BACK", command=self.instructionsToHome, bg='white', font=("Calibri", 12, 'bold'))
        self.exit_instructions.grid(row=6, column=1)

        self.fourthWin.withdraw()  # Hide this window until we need it!
        self.fourthWin.protocol("WM_DELETE_WINDOW", self.endProgram)
###################################################################################################################
        #instructions page (check in) instructions

        self.sixthWin = Toplevel()
        self.sixthWin.configure(bg='white')
#######
        self.check_in_message1_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message1_frame.grid(row=1, column=1)

        self.check_in_message2_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message2_frame.grid(row=2, column=1)

        self.check_in_message3_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message3_frame.grid(row=3, column=1)

        self.check_in_message4_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message4_frame.grid(row=4, column=1)

        self.check_in_message5_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message5_frame.grid(row=5, column=1)

        self.check_in_message6_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message6_frame.grid(row=6, column=1)

        self.check_in_message7_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message7_frame.grid(row=7, column=1)

        self.check_in_message8_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message8_frame.grid(row=8, column=1)

        self.check_in_message9_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message9_frame.grid(row=9, column=1)

        self.check_in_message10_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message10_frame.grid(row=10, column=1)

        self.check_in_message11_frame = Frame(self.sixthWin, bg='white')
        self.check_in_message11_frame.grid(row=11, column=1)
#######
        self.check_in_message1 = Label(self.check_in_message1_frame, bg='white', text='Name- Enter your desired name into the box', font=("Calibri", 12))
        self.check_in_message1.grid(row=1, column=1, padx=10, pady=10)

        self.check_in_message2 = Label(self.check_in_message2_frame, bg='white', text='Gender- Select your gender. Otherwise select "Prefer not to say" option', font=("Calibri", 12))
        self.check_in_message2.grid(row=2, column=1, padx=10, pady=10)

        self.check_in_message3 = Label(self.check_in_message3_frame, bg='white', text='Number of occupants- Select how many people will be in the room', font=("Calibri", 12))
        self.check_in_message3.grid(row=3, column=1, padx=10, pady=10)

        self.check_in_message4 = Label(self.check_in_message4_frame, bg='white', text='Length of stay- Enter your desired length of stay in the box. Maximum 60 days.', font=("Calibri", 12))
        self.check_in_message4.grid(row=4, column=1, padx=10, pady=10)

        self.check_in_message5 = Label(self.check_in_message5_frame, bg='white', text='Type of room- Select your desired room type;', font=("Calibri", 12))
        self.check_in_message5.grid(row=5, column=1, padx=10, pady=10)

        self.check_in_message6 = Label(self.check_in_message6_frame, bg='white', text='Single Suite- 1 single bed, 1 bathroom $40p/n', font=("Calibri", 12))
        self.check_in_message6.grid(row=6, column=1)

        self.check_in_message7 = Label(self.check_in_message7_frame, bg='white', text='Double Suite- 2 single beds, 1 bathroom $60p/n', font=("Calibri", 12))
        self.check_in_message7.grid(row=7, column=1)

        self.check_in_message8 = Label(self.check_in_message8_frame, bg='white', text='Queen Suite- 1 queen bed, 2 bathrooms $100p/n', font=("Calibri", 12))
        self.check_in_message8.grid(row=8, column=1)

        self.check_in_message9 = Label(self.check_in_message9_frame, bg='white', text='Executive Suite- 1 king bed, 1 single bed, 2 bathrooms $150p/n', font=("Calibri", 12))
        self.check_in_message9.grid(row=9, column=1)

        self.check_in_message10 = Label(self.check_in_message10_frame, bg='white', text='Additional add ons- Optional add-ons. Select your desired options (additional fee)', font=("Calibri", 12))
        self.check_in_message10.grid(row=10, column=1, padx=10, pady=10)

        self.check_in_message11 = Label(self.check_in_message11_frame, bg='white', text='Ensure proper details are given', font=("Calibri", 12, 'bold'))
        self.check_in_message11.grid(row=11, column=1, padx=10, pady=10)


        self.back_button1 = Button(self.sixthWin, text='BACK', bg='white', font=("Calibri", 12, 'bold'), command=self.checkInInstructionsToInstructions)
        self.back_button1.grid(row=12, column=1)

        self.sixthWin.withdraw()  # Hide this window until we need it!
        self.sixthWin.protocol("WM_DELETE_WINDOW", self.endProgram)
###################################################################################################################
        #instructions page (check out) instructions

        self.seventhWin = Toplevel()
        self.seventhWin.configure(bg='white')
#######
        self.check_out_message1_frame = Frame(self.seventhWin, bg='white')
        self.check_out_message1_frame.grid(row=1, column=1)

        self.check_out_message2_frame = Frame(self.seventhWin, bg='white')
        self.check_out_message2_frame.grid(row=2, column=1)

        self.check_out_message3_frame = Frame(self.seventhWin, bg='white')
        self.check_out_message3_frame.grid(row=3, column=1)

        self.check_out_message4_frame = Frame(self.seventhWin, bg='white')
        self.check_out_message4_frame.grid(row=4, column=1)
#######
        self.check_out_message1 = Label(self.check_out_message1_frame, bg='white', font=("Calibri", 12), text='Name- Enter your name. The same name entred in CHECK IN')
        self.check_out_message1.grid(row=1, column=1, padx=10, pady=10)

        self.check_out_message2 = Label(self.check_out_message2_frame, bg='white', font=("Calibri", 12), text='Room Number- Enter your designated room number')
        self.check_out_message2.grid(row=2, column=1, padx=10, pady=10)

        self.check_out_message3 = Label(self.check_out_message3_frame, bg='white', font=("Calibri", 12), text='Payment Type- Select your desired payment option')
        self.check_out_message3.grid(row=3, column=1, padx=10, pady=10)

        self.check_out_message4 = Label(self.check_out_message4_frame, bg='white', font=("Calibri", 12, 'bold'), text="Ensure correct details are provided, otherwise you won't be checked out")
        self.check_out_message4.grid(row=4, column=1, padx=10, pady=10)

        self.back_button2 = Button(self.seventhWin, text='BACK', bg='white', font=("Calibri", 12, 'bold'), command=self.checkOutInstructionsToInstructions)
        self.back_button2.grid(row=5, column=1)
        
        self.seventhWin.withdraw()  # Hide this window until we need it!
        self.seventhWin.protocol("WM_DELETE_WINDOW", self.endProgram)
###################################################################################################################
#HELP PAGE CODE

        self.fifthWin = Toplevel()
        self.fifthWin.configure(bg="white")

        #title for the page (label widget)
        self.help_title = Label(self.fifthWin, text="Help Page", font=("Calibri", 20, 'bold'), bg='white')
        self.help_title.grid()
        
        #the code below is for the text that will appear
        self.help_line_1 = Label(self.fifthWin, text="If you need any assistance or would like to submit any feedback", bg='white', font=("Calibri", 14))
        self.help_line_1.grid()
        self.help_line_2 = Label(self.fifthWin, text="please contact any of the below support services", bg='white', font=("Calibri", 14))
        self.help_line_2.grid()
        self.help_line_3 = Label(self.fifthWin, text="Name- Srikar Danthurty ", bg='white', font=("Calibri", 12, 'bold'))
        self.help_line_3.grid(padx=10, pady=10)
        self.help_line_4 = Label(self.fifthWin, text="Website- https://web3.homebushbo-h.schools.nsw.edu.au", bg='white', font=("Calibri", 12, 'bold'))
        self.help_line_4.grid(padx=10, pady=10)

        self.help_line_5 = Label(self.fifthWin, text="Email- srikar.danthurty@education.nsw.gov.au", bg='white', font=("Calibri", 12, 'bold'))
        self.help_line_5.grid(padx=10, pady=10)
        self.help_line_6 = Label(self.fifthWin, text="Phone- (02) 9764 3611", bg='white', font=("Calibri", 12, 'bold'))
        self.help_line_6.grid(padx=10, pady=10)
        
        #go back button
        self.exit_help_page = Button(self.fifthWin, text="BACK", command=self.helpToHome, bg='white', font=("Calibri", 12, 'bold'))
        self.exit_help_page.grid()

        self.fifthWin.withdraw()  # Hide this window until we need it!
        self.fifthWin.protocol("WM_DELETE_WINDOW", self.endProgram)
###################################################################################################################
#DEFINITIONS CODE


#//////////DEFINITIONS TO TAKE USER FROM MAIN PAGE TO ANY OF THE OPTIONS\\\\\\\\\\
        
#this definition takes user from MAIN PAGE to CHECK IN page
    def checkInPage(self):
        print ('switching')
        self.mainWin.withdraw()
        self.secondWin.deiconify()

#this definition to go from MAIN page to CHECK OUT page
    def checkOutPage(self):
        print('switching')
        self.mainWin.withdraw()
        self.thirdWin.deiconify()

#definition to go from MAIN PAGE to INSTRUCTIONS page
    def instructionsPage(self):
        print ('switching')
        self.mainWin.withdraw()
        self.fourthWin.deiconify()

#this definition to go from MAIN page to HELP page
    def helpPage(self):
        print("switching")
        self.mainWin.withdraw()
        self.fifthWin.deiconify()


#//////////DEFINITIONS TO TAKE USER FROM OPTIONS TO HOME PAGE\\\\\\\\\\        

#definition to go from CHECK IN page to MAIN page
    def checkInToHome(self):
        print ('switching')
        self.var.set(0)
        self.var1.set(0)
        self.var2.set(0)
        self.var3.set(0)
        self.var4.set(0)
        self.var5.set(0)
        self.var6.set(0)
        self.var7.set(0)
        self.var8.set(0)
        self.secondWin.withdraw()
        self.first_name_entry.delete(0, END)
        self.incorrect_message_label['text'] = " "
        self.stay_length_number.delete(0, END)
        self.mainWin.deiconify()

#definitions to go from CHECK OUT page to MAIN page
    def checkOutToHome(self):
        print('switching')
        self.check_out_name.delete(0, END)
        self.room_number.delete(0, END)
        self.message_label['text']= " "
        self.var9.set(0)
        self.thirdWin.withdraw()
        self.mainWin.deiconify()
        
#definition to go from INSTRUCTIONS page to MAIN page
    def instructionsToHome(self):
        print('switching')
        self.fourthWin.withdraw()
        self.mainWin.deiconify()

#definition to go from HELP page to MAIN page
    def helpToHome(self):
        print('switching')
        self.fifthWin.withdraw()
        self.mainWin.deiconify()


#//////////DEFINITIONS TO TAKE USER FROM CHECK IN/OUT TO SUBMISSION/PAYMENT PAGE\\\\\\\\\\

#definition from SUBMIT (check in) to SUBMISSION PAGE
    def submitToConfirm(self):
        print('switching')

        empty_entry = self.first_name_entry.get()
        if len (empty_entry)<1:
            self.incorrect_message_label['text'] = "Invalid entry. Check details and try again"
            return

        empty_entry2 = self.stay_length_number.get()
        if len (empty_entry2)<1:
            self.incorrect_message_label['text'] = "Invalid entry. Check details and try again"
            return

        name_of_user = self.first_name_entry.get()
        
        number_of_days = self.stay_length_number.get()
        days_stayed = int(number_of_days)

        #this is for the display text of what the user selected
        gender_of_user = self.var.get()
        selection = self.var.get()
        if selection == 1:
            self.user_gender_ci['text']= 'Gender: Male'
        elif selection == 2:
            self.user_gender_ci['text']= 'Gender: Female'
        elif selection == 3:
            self.user_gender_ci['text']= 'Gender: Prefer not to say'
        elif selection == 0:
            self.incorrect_message_label['text'] = "Select gender"
            print('enter correct')
            return

        user_chosen_room = self.var1.get()
        selection4 = self.var1.get()
        if selection4 == 40:
            self.user_room_type_ci['text']= 'Chosen room: Single Suite'
        elif selection4 == 60:
            self.user_room_type_ci['text']= 'Chosen room: Double Suite'
        elif selection4 == 100:
            self.user_room_type_ci['text']= 'Chosen room: Queen Suite'
        elif selection4 == 150:
            self.user_room_type_ci['text']= 'Chosen room: Executive Suite'
        elif selection4 == 0:
            self.incorrect_message_label['text'] = "Select room type"
            print('enter correct')
            return
            
        

        #this is for the display text of what the user selected
        occupants_number = self.var8.get()
        selection2 = self.var8.get()
        if selection2 == 1:
            self.how_many_people['text']= 'Number of people: 1'
        elif selection2 == 2:
            self.how_many_people['text']= 'Number of people: 2'
        elif selection2 == 3:
            self.how_many_people['text']= 'Number of people: 3'
        elif selection2 == 4:
            self.how_many_people['text']= 'Number of people: 4'
        elif selection2 == 0:
            self.incorrect_message_label['text']= 'Select number of occupants'
            return
            
        
        #tis is for all check buttons do similar
            

        occupant_number = self.var8.get()
        number_of_occupants = int(occupant_number)
        
        self.user_grand_total = ((self.var1.get() +  self.var2.get() +  self.var3.get() +  self.var4.get() +  self.var5.get() + self.var6.get() + self.var7.get())*days_stayed)
        
        
        self.room_number_gen = randint(1,51)

        
        self.add_ons_text = ''

        if self.var2.get():
            #self.selected_options1['text']=('WIFI selected')
            self.add_ons_text += 'WIFI access\n'
            self.user_grand_total += 2

        if self.var3.get():
            #self.selected_options2['text']=('POOL ACCESS selected')
            self.add_ons_text += 'Pool access\n'
            self.user_grand_total += 5

        if self.var4.get():
            #self.selected_options3['text']=('PARKING selected')
            self.add_ons_text += 'Parking access\n'
            self.user_grand_total += 2

        if self.var5.get():
            #self.selected_options4['text']=('ROOM SERVICE selected')
            self.add_ons_text += 'Room Service\n'
            self.user_grand_total += 5
            
        if self.var6.get():
            #self.selected_options5['text']=('AC selected')
            self.add_ons_text +=  'AC\n'
            self.user_grand_total += 1
            
        if self.var7.get():
            #self.selected_options6['text']=('TV selected')
            self.add_ons_text += 'TV\n'
            self.user_grand_total += 1

        self.selected_options['text']= self.add_ons_text
            

        self.data_store[name_of_user]= {'gender': gender_of_user, 'Total': self.user_grand_total, 'room no': int(self.room_number_gen), 'length of stay':int(number_of_days)}

        
        if int(self.stay_length_number.get())>60:
            self.incorrect_message_label['text']= 'Invalid length of stay. Check details and try again'
            print('enter correct details')
            return
        if int(self.stay_length_number.get())<1:
            self.incorrect_message_label['text']= 'Invalid length of stay. Check details and try again'
            print('enter correct details')
            return

        

        self.user_name['text']= "Name: {0}".format( self.first_name_entry.get())
        self.stay_of_user['text']="Length of stay: {0} days".format(self.stay_length_number.get())
        self.user_room_number['text']="Room Number: {0}".format(self.room_number_gen)

        self.var.set(0)
        self.var1.set(0)
        self.var2.set(0)
        self.var3.set(0)
        self.var4.set(0)
        self.var5.set(0)
        self.var6.set(0)
        self.var7.set(0)
        self.var8.set(0)
        #do the same for all the var(s)

        #self.test_label_var.set( str(self.data_store) )
        self.secondWin.withdraw()
        self.first_name_entry.delete(0, END)
        self.stay_length_number.delete(0, END)
        self.submissionWin_check_in.deiconify()

#definition from SUBMIT (check out) to SUBMISSION PAGE
    def submitToPayment(self):


        empty_entry3 = self.check_out_name.get()
        if len (empty_entry3)< 1:
            self.message_label['text']= "Invalid entry. Check details and try again"

        empty_entry4 = self.room_number.get()
        if len (empty_entry4)< 1:
            self.message_label['text']= "Invalid entry. Check details and try again"
            
            
        
        key_name = self.check_out_name.get()
        if key_name not in self.data_store.keys():
            self.message_label['text']= "Invalid name. Check details and try again"
            print('name %s not found in database' % key_name )
            return
        user_details = self.data_store[key_name]
        print( "checking %d vs %d" % ( user_details['room no'],  int(self.room_number.get() )) )
        if user_details['room no'] != int(self.room_number.get() ) :
            self.message_label['text']= "Invalid room number. Check details and try again"
            return
        else:
            self.total_payment['text']= "Grand Total $" + str(user_details['Total'])
            
        option_type = self.var9.get()
        selection3 = self.var9.get()
        if selection3 == 1:
            self.type_of_payment['text']= "Payment Option: Cash"
        if selection3 == 2:
            self.type_of_payment['text']= "Payment Option: Card"
        if selection3 == 3:
            self.type_of_payment['text']= "Payment Option: Other"
        if selection3 == 0:
            self.message_label['text']= "Select payment type"
            return

        self.check_out_name.delete(0, END)
        self.room_number.delete(0, END)
        self.var9.set(0)
        self.thirdWin.withdraw()
        self.submissionWin_check_out.deiconify()


#//////////DEFINITIONS TO TAKE USER FROM SUBMISSION/PAYMENT PAGE TO MAIN PAGE\\\\\\\\\\

#definition to go from submission page to MAIN page
    def confirmToCheckIn(self):
        print('switching')
        self.submissionWin_check_in.withdraw()
        self.mainWin.deiconify()

#definition to go from payment page to MAIN page
    def paymentToMain(self):
        print('switching')
        self.submissionWin_check_out.withdraw()
        self.mainWin.deiconify()


#//////////DEFINITIONS TO CLOSE PAGES\\\\\\\\\\

#definition to close the submission/payment page
    def closepage(self):
        self.submissionWin_check_in.withdraw()
        self.submissionWin_check_out.withdraw()

#this definition allows user to exit the window
    def endProgram(self):
        print("switching")
        self.mainWin.destroy()

#//////////DEFINITIONS TO TAKE USER FROM INSTRUCTIONS PAGE TO CHECK IN/OUT INSTRUCTIONS PAGE\\\\\\\\\\
    def checkInInstructions(self):
        self.fourthWin.withdraw()
        self.sixthWin.deiconify()

    def checkOutInstructions(self):
        self.fourthWin.withdraw()
        self.seventhWin.deiconify()

#//////////DEFINITIONS TO TAKE USER FROM CHECK IN/OUT INSTRUCTIONS PAGE TO INSTRUCTIONS PAGE\\\\\\\\\\
    def checkInInstructionsToInstructions(self):
        self.sixthWin.withdraw()
        self.fourthWin.deiconify()

    def checkOutInstructionsToInstructions(self):
        self.seventhWin.withdraw()
        self.fourthWin.deiconify()
        
mw = Tk()
myApp = WinDos(mw)
mw.mainloop()
print('All Done!')
